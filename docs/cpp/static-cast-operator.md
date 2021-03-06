---
title: static_cast 运算符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a0cd6ea7e2268940febca9e1e564f30d29dcff0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="staticcast-operator"></a>static_cast 运算符
将转换*表达式*为的类型*类型 id，*仅根据同时出现在表达式的类型。  
  
## <a name="syntax"></a>语法  
  
```  
static_cast <type-id> ( expression )   
```  
  
## <a name="remarks"></a>备注  
 在标准 C++ 中，不进行运行时类型检查来帮助确保转换的安全。 在 C++/CX 中，将执行编译时和运行时检查。 有关详细信息，请参阅[强制转换](casting.md)。  
  
 `static_cast` 运算符可用于将指向基类的指针转换为指向派生类的指针等操作。 此类转换并非始终安全。  
  
 通常使用 `static_cast` 转换数值数据类型，例如将枚举型转换为整型或将整型转换为浮点型，而且你能确定参与转换的数据类型。 `static_cast` 转换安全性不如 `dynamic_cast` 转换，因为 `static_cast` 不执行运行时类型检查，而 `dynamic_cast` 执行该检查。 对不明确的指针的 `dynamic_cast` 将失败，而 `static_cast` 的返回结果看似没有问题，这是危险的。 尽管 `dynamic_cast` 转换更加安全，但是 `dynamic_cast` 只适用于指针或引用，而且运行时类型检查也是一项开销。 有关详细信息，请参阅[dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)。  
  
 在下面的示例中，因为 `D* pd2 = static_cast<D*>(pb);` 可能有不在 `D` 内的字段和方法，所以行 `B` 不安全。 但是，因为 `B* pb2 = static_cast<B*>(pd);` 始终包含所有 `D`，所以行 `B` 是安全的转换。  
  
```  
// static_cast_Operator.cpp  
// compile with: /LD  
class B {};  
  
class D : public B {};  
  
void f(B* pb, D* pd) {  
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields  
                                   // and methods that are not in B.  
  
   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always  
                                   // contains all of B.  
}  
```  
  
 与此相反[dynamic_cast](../cpp/dynamic-cast-operator.md)，不运行时进行检查上`static_cast`的转换`pb`。 由 `pb` 指向的对象可能不是 `D` 类型的对象，在这种情况下使用 `*pd2` 会是灾难性的。 例如，调用 `D` 类（而非 `B` 类）的成员函数可能会导致访问冲突。  
  
 `dynamic_cast` 和 `static_cast` 运算符可以在整个类层次结构中移动指针。 然而，`static_cast` 完全依赖于转换语句提供的信息，因此可能不安全。 例如：  
  
```  
// static_cast_Operator_2.cpp  
// compile with: /LD /GR  
class B {  
public:  
   virtual void Test(){}  
};  
class D : public B {};  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  
   D* pd2 = static_cast<D*>(pb);  
}  
```  
  
 如果 `pb` 确实指向 `D` 类型的对象，则 `pd1` 和 `pd2` 将获取相同的值。 如果 `pb == 0`，它们也将获取相同的值。  
  
 如果 `pb` 指向 `B` 类型的对象，而非指向完整的 `D` 类，则 `dynamic_cast` 足以判断返回零。 但是，`static_cast` 依赖于程序员的断言，即 `pb` 指向 `D` 类型的对象，因而只是返回指向那个假定的 `D` 对象的指针。  
  
 因此，`static_cast` 可以反向执行隐式转换，而在这种情况下结果是不确定的。 这需要程序员来验证 `static_cast` 转换的结果是否安全。  
  
 该行为也适用于类以外的类型。 例如，`static_cast` 可用于将 int 转换为 `char`。 但是，得到的 `char` 可能没有足够的位来保存整个 `int` 值。 同样，它仍将需要程序员来验证的结果`static_cast`转换是安全。  
  
 `static_cast` 运算符还可用于执行任何隐式转换，包括标准转换和用户定义的转换。 例如：  
  
```  
// static_cast_Operator_3.cpp  
// compile with: /LD /GR  
typedef unsigned char BYTE;  
  
void f() {  
   char ch;  
   int i = 65;  
   float f = 2.5;  
   double dbl;  
  
   ch = static_cast<char>(i);   // int to char  
   dbl = static_cast<double>(f);   // float to double  
   i = static_cast<BYTE>(ch);  
}  
```  
  
 `static_cast` 运算符可以将整数值显式转换为枚举类型。 如果整型值不在枚举值的范围内，生成的枚举值是不确定的。  
  
 `static_cast` 运算符将 null 指针值转换为目标类型的 null 指针值。  
  
 任何表达式都可以通过 `static_cast` 运算符显式转换为 void 类型。 目标 void 类型可以选择性地包含 `const`、`volatile` 或 `__unaligned` 特性。  
  
 `static_cast` 运算符无法转换掉 `const`、`volatile` 或 `__unaligned` 特性。 请参阅[const_cast 运算符](../cpp/const-cast-operator.md)有关移除这些特性的信息。  
  
 由于在一个重定位垃圾回收器顶部执行无检查转换的危险，你只应在确信代码将正常运行的时候，在性能关键代码中使用 `static_cast`。 如果必须使用`static_cast`在发布模式下，替换它[safe_cast](../windows/safe-cast-cpp-component-extensions.md)在调试版本中，以确保成功。  
  
## <a name="see-also"></a>请参阅  
 [强制转换运算符](../cpp/casting-operators.md)   
 [关键字](../cpp/keywords-cpp.md)