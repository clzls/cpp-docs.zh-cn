---
title: 示例多线程 C 程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4706f6cd-ff9c-4dbf-99a2-1c999b568f17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1584d52f9ea543c95363a0f7f03cdad80442ee1c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="sample-multithread-c-program"></a>多线程 C 程序示例
Bounce.c 是创建一个新的示例多线程程序线程每次字母或**A**已类型化。 每个线程退回笑脸在屏幕的不同颜色。 可以创建多达 32 个线程。 发生的程序正常终止时`q`或**Q**已类型化。 编译和链接 Bounce.c 有关的信息，请参阅[编译和链接多线程程序](../parallel/compiling-and-linking-multithread-programs.md)。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
// sample_multithread_c_program.c  
// compile with: /c  
//  
//  Bounce - Creates a new thread each time the letter 'a' is typed.  
//  Each thread bounces a happy face of a different color around  
//  the screen. All threads are terminated when the letter 'Q' is  
//  entered.  
//  
  
#include <windows.h>  
#include <stdlib.h>  
#include <string.h>  
#include <stdio.h>  
#include <conio.h>  
#include <process.h>  
  
#define MAX_THREADS  32  
  
// The function getrandom returns a random number between   
// min and max, which must be in integer range.  
#define getrandom( min, max ) (SHORT)((rand() % (int)(((max) + 1) - \  
                               (min))) + (min))  
  
int main( void );                    // Thread 1: main   
void KbdFunc( void  );               // Keyboard input, thread dispatch  
void BounceProc( void * MyID );      // Threads 2 to n: display   
void ClearScreen( void );            // Screen clear   
void ShutDown( void );               // Program shutdown   
void WriteTitle( int ThreadNum );    // Display title bar information   
  
HANDLE  hConsoleOut;                 // Handle to the console   
HANDLE  hRunMutex;                   // "Keep Running" mutex   
HANDLE  hScreenMutex;                // "Screen update" mutex  
int     ThreadNr;                    // Number of threads started   
CONSOLE_SCREEN_BUFFER_INFO csbiInfo; // Console information  
  
int main() // Thread One   
{  
    // Get display screen information & clear the screen.  
    hConsoleOut = GetStdHandle( STD_OUTPUT_HANDLE );  
    GetConsoleScreenBufferInfo( hConsoleOut, &csbiInfo );  
    ClearScreen();  
    WriteTitle( 0 );  
  
    // Create the mutexes and reset thread count.  
    hScreenMutex = CreateMutex( NULL, FALSE, NULL );  // Cleared   
    hRunMutex = CreateMutex( NULL, TRUE, NULL );      // Set   
    ThreadNr = 0;  
  
    // Start waiting for keyboard input to dispatch threads or exit.  
    KbdFunc();  
  
    // All threads done. Clean up handles.  
    CloseHandle( hScreenMutex );  
    CloseHandle( hRunMutex );  
    CloseHandle( hConsoleOut );  
}  
  
void ShutDown( void ) // Shut down threads   
{  
    while ( ThreadNr > 0 )  
    {  
        // Tell thread to die and record its death.  
        ReleaseMutex( hRunMutex );  
        ThreadNr--;     
    }  
  
    // Clean up display when done  
    WaitForSingleObject( hScreenMutex, INFINITE );  
    ClearScreen();  
}  
  
void KbdFunc( void ) // Dispatch and count threads.  
{  
    int         KeyInfo;  
  
    do  
    {  
        KeyInfo = _getch();  
        if ( tolower( KeyInfo ) == 'a' &&   
             ThreadNr < MAX_THREADS )  
        {  
            ThreadNr++;  
            _beginthread( BounceProc, 0, &ThreadNr );  
            WriteTitle( ThreadNr );  
        }  
    } while( tolower( KeyInfo ) != 'q' );  
  
    ShutDown();  
}  
  
void BounceProc( void *pMyID )  
{  
    char    MyCell, OldCell;  
    WORD    MyAttrib, OldAttrib;  
    char    BlankCell = 0x20;  
    COORD   Coords, Delta;  
    COORD   Old = {0,0};  
    DWORD   Dummy;  
    char    *MyID = (char*)pMyID;  
  
    // Generate update increments and initial   
    // display coordinates.  
    srand( (unsigned int) *MyID * 3 );  
  
    Coords.X = getrandom( 0, csbiInfo.dwSize.X - 1 );  
    Coords.Y = getrandom( 0, csbiInfo.dwSize.Y - 1 );  
    Delta.X = getrandom( -3, 3 );  
    Delta.Y = getrandom( -3, 3 );  
  
    // Set up "happy face" & generate color   
    // attribute from thread number.  
    if( *MyID > 16)  
        MyCell = 0x01;          // outline face   
    else  
        MyCell = 0x02;          // solid face   
    MyAttrib =  *MyID & 0x0F;   // force black background   
  
    do  
    {  
        // Wait for display to be available, then lock it.  
        WaitForSingleObject( hScreenMutex, INFINITE );  
  
        // If we still occupy the old screen position, blank it out.   
        ReadConsoleOutputCharacter( hConsoleOut, &OldCell, 1,   
                                    Old, &Dummy );  
        ReadConsoleOutputAttribute( hConsoleOut, &OldAttrib, 1,   
                                    Old, &Dummy );  
        if (( OldCell == MyCell ) && (OldAttrib == MyAttrib))  
            WriteConsoleOutputCharacter( hConsoleOut, &BlankCell, 1,  
                                         Old, &Dummy );  
  
        // Draw new face, then clear screen lock   
        WriteConsoleOutputCharacter( hConsoleOut, &MyCell, 1,   
                                     Coords, &Dummy );  
        WriteConsoleOutputAttribute( hConsoleOut, &MyAttrib, 1,   
                                     Coords, &Dummy );  
        ReleaseMutex( hScreenMutex );  
  
        // Increment the coordinates for next placement of the block.   
        Old.X = Coords.X;  
        Old.Y = Coords.Y;  
        Coords.X += Delta.X;  
        Coords.Y += Delta.Y;  
  
        // If we are about to go off the screen, reverse direction   
        if( Coords.X < 0 || Coords.X >= csbiInfo.dwSize.X )  
        {  
            Delta.X = -Delta.X;  
            Beep( 400, 50 );  
        }  
        if( Coords.Y < 0 || Coords.Y > csbiInfo.dwSize.Y )  
        {  
            Delta.Y = -Delta.Y;  
            Beep( 600, 50 );  
        }  
    }  
    // Repeat while RunMutex is still taken.   
    while ( WaitForSingleObject( hRunMutex, 75L ) == WAIT_TIMEOUT );  
}  
  
void WriteTitle( int ThreadNum )  
{  
    enum {   
        sizeOfNThreadMsg = 80   
    };  
    char    NThreadMsg[sizeOfNThreadMsg];  
  
    sprintf_s( NThreadMsg, sizeOfNThreadMsg,   
               "Threads running: %02d.  Press 'A' "  
               "to start a thread,'Q' to quit.", ThreadNum );  
    SetConsoleTitle( NThreadMsg );  
}  
  
void ClearScreen( void )  
{  
    DWORD    dummy;  
    COORD    Home = { 0, 0 };  
    FillConsoleOutputCharacter( hConsoleOut, ' ',   
                                csbiInfo.dwSize.X * csbiInfo.dwSize.Y,   
                                Home, &dummy );  
}  
```  
  
### <a name="input"></a>输入  
  
```  
a  
q  
```  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)