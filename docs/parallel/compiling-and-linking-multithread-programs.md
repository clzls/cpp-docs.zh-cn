---
title: 编译和链接多线程程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c77cb217fe841e15f4c7470340bd3fbb502f6a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="compiling-and-linking-multithread-programs"></a>编译和链接多线程程序
中引入 Bounce.c 程序[多线程 C 程序示例](../parallel/sample-multithread-c-program.md)。  
  
 程序被编译多线程默认情况下。  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>若要编译和链接的开发环境中的多线程程序从 Bounce.c  
  
1.  在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。  
  
2.  在**项目类型**窗格中，单击**Win32**。  
  
3.  在**模板**窗格中，单击**Win32 控制台应用程序**，并将其命名项目。  
  
4.  将包含文件添加到项目的 C 源代码。  
  
5.  上**生成**菜单上，通过单击生成项目**生成**命令。  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>若要编译和链接多线程程序 Bounce.c 从命令行  
  
1.  编译和链接程序：  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)