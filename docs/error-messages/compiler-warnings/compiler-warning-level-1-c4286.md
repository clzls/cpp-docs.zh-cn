---
title: 编译器警告 （等级 1） C4286 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4286
dev_langs:
- C++
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2dab6c5c28809108e178ec7792a68a570ece14ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4286"></a>编译器警告（等级 1）C4286
type1： 由基类 (type2) 在行号上捕获  
  
 指定的异常类型由上一个处理程序处理。 第二个 catch 的类型派生自的第一个类型。 异常的基类捕获异常的派生类。  
  
## <a name="example"></a>示例  
  
```  
//C4286.cpp  
// compile with: /W1  
#include <eh.h>  
class C {};  
class D : public  C {};  
int main()  
{  
    try  
    {  
        throw "ooops!";  
    }  
    catch( C ) {}  
    catch( D ) {}  // warning C4286, D is derived from C  
}  
```