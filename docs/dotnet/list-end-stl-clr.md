---
title: 'list:: end (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::end
dev_langs:
- C++
helpviewer_keywords:
- end member [STL/CLR]
ms.assetid: c3444164-2c6e-4cbd-8765-1ce7d30fc43e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bcccbb2332988e1b2a203a61688b0ebceb3defb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="listend-stlclr"></a>list::end (STL/CLR)
指定受控序列的末尾。  
  
## <a name="syntax"></a>语法  
  
```  
iterator end();  
```  
  
## <a name="remarks"></a>备注  
 成员函数返回一个随机访问迭代器，它指向刚超出受控序列的末尾。 用于获取指定的受控序列中; 末尾的迭代器其状态不更改如果更改了受控序列的长度。  
  
## <a name="example"></a>示例  
  
```  
// cliext_list_end.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::list<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
 a x y  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: back (STL/CLR)](../dotnet/list-back-stl-clr.md)   
 [list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)   
 [list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md)