---
title: 编译器错误 C2229 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2229
dev_langs:
- C++
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c61708e7e67db39f85b1ff782e8945facc2b9568
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2229"></a>编译器错误 C2229
类型 identifier 具有非法的零大小的数组  
  
 结构或位域的成员包含不是最后一个成员的大小为零的数组。  
  
 由于你可以有零大小的数组作为结构的最后一个成员，必须指定其大小，当分配结构。  
  
 如果零大小的数组不是结构的最后一个成员，则编译器无法计算剩余的字段的偏移量。  
  
 下面的示例生成 C2229:  
  
```  
// C2229.cpp  
struct S {  
   int a[0];  // C2229  zero-sized array  
   int b[1];  
};  
  
struct S2 {  
   int a;  
   int b[0];  
};  
  
int main() {  
   // allocate 7 elements for b field  
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];  
   s2->b[6] = 100;  
}  
```