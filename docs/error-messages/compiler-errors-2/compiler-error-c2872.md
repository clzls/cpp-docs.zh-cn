---
title: 编译器错误 C2872 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 636f263382c41806e04c50c0770340305a3013ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2872"></a>编译器错误 C2872
*符号*： 不明确的符号  
  
编译器无法确定所引用的符号。 具有指定名称的多个符号处于范围。 编译器找到不明确的符号，请参阅以下错误消息中的文件位置和声明说明。 若要解决此问题，你可以完全限定的不明确的符号通过使用其命名空间，例如，`std::byte`或`::byte`。 你还可以使用[命名空间别名](../../cpp/namespaces-cpp.md#namespace_aliases)，以为提供一个包含命名空间使用的方便短名称消除歧义在源代码中的符号。  
  
如果标头文件包含，则会发生 C2872 [using 指令](../../cpp/namespaces-cpp.md#using_directives)，并包含了一个后续标头文件，其中包含在指定的命名空间中也是一种`using`指令。 指定`using`指令仅在所有标头文件指定与后`#include`。  
  
 有关 C2872 的详细信息，请参阅知识库文章[PRB： 编译器错误时你用于 #import Visual c + +.NET 中的 XML](http://support.microsoft.com/kb/316317)和["错误 C2872: 平台： 不明确的符号"使用时的错误消息在 Visual Studio 2013 的 Windows::Foundation::Metadata 命名空间](https://support.microsoft.com/kb/2890859)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2872，因为不明确的引用名为的变量，所以`i`; 两个具有相同名称的变量都位于作用域：  
  
```cpp  
// C2872.cpp  
// compile with: cl /EHsc C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok, uses i from global namespace  
   A::i++;   // ok, uses i from namespace A  
   i++;   // C2872 ambiguous: ::i or A::i? 
   // To fix this issue, use the fully qualified name
   // for the intended variable. 
}  
```