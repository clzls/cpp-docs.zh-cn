---
title: ref new、 gcnew （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9533675d2894b3c3d99e3fb57abded8ea4e99d7a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new、gcnew（C++ 组件扩展）
`ref new`聚合关键字分配进行垃圾回收时在对象变为不可访问，并返回的句柄类型的实例 ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) 到分配的对象。  
  
## <a name="all-runtimes"></a>所有运行时  
 `ref new` 分配的类型的实例的内存会自动释放。  
  
 如果无法分配内存，则 `ref new` 操作会引发 `OutOfMemoryException`。  
  
 有关如何分配和释放本机 c + + 类型的内存的详细信息，请参阅[新和 delete 运算符](../cpp/new-and-delete-operators.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 使用 `ref new` 可为要自动管理其生存期的 Windows 运行时对象分配内存。 对象会在其引用计数变为零（这会在引用的最后一个副本超出范围之后发生）时自动释放。 有关详细信息，请参阅[Ref 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 托管类型（引用或值类型）的内存由 `gcnew` 分配，使用垃圾回收进行释放。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的示例使用 `gcnew` 分配 Message 对象。  
  
```  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 **示例**  
  
 下面的示例使用 `gcnew` 创建装箱值类型以供使用（如引用类型）。  
  
```  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
 **输出**  
  
```Output  
32  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)