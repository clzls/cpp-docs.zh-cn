---
title: 编译器错误 C3320 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08810d38b74081cfb8573d1e33ea3a8ec4dabd4c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3320"></a>编译器错误 C3320
“type”：类型不能和模块的“name”属性同名  
  
导出的用户定义的类型 (UDT)，这可能是结构、 类、 枚举或联合，不能将相同的名称作为参数传递给[模块](../../windows/module-cpp.md)特性的名称属性。  
  
## <a name="example"></a>示例  
以下示例生成 C3320：  
  
```cpp  
// C3320.cpp  
#include "unknwn.h"  
[module(name="xx")];  
  
[export] struct xx {   // C3320  
// Try the following line instead  
// [export] struct yy {  
   int i;  
};  
```