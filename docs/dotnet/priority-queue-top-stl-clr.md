---
title: 'priority_queue:: top (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::top
dev_langs:
- C++
helpviewer_keywords:
- top member [STL/CLR]
ms.assetid: e45211d5-e6df-4c03-97fd-57afb87af58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7cf02100bf08ad78452368f633443b8d738730a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="priorityqueuetop-stlclr"></a>priority_queue::top (STL/CLR)
访问优先级最高的元素。  
  
## <a name="syntax"></a>语法  
  
```  
reference top();  
```  
  
## <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的顶部 （最高优先级） 元素的引用。 用于访问优先级最高的元素中，当你知道它存在。  
  
## <a name="example"></a>示例  
  
```  
// cliext_priority_queue_top.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
top() = c  
 x a b  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::top_item (STL/CLR)](../dotnet/priority-queue-top-item-stl-clr.md)