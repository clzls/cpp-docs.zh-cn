---
title: 编译器错误 C3713 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3713
dev_langs:
- C++
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f0e919add44075516deedfb339c8e1d7487f6ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3713"></a>编译器错误 C3713
method： 事件处理程序方法必须具有相同的函数参数作为源 method  
  
 您定义未使用相同的参数作为源事件方法的事件处理程序方法。 若要修复此错误，给予事件处理程序方法与这些源事件方法相同的参数。  
  
 下面的示例生成 C3713:  
  
```  
// C3713.cpp  
// compile with: /c  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void event1(int nValue);  
   // try the following line instead  
   // __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void handler1() {}  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713  
   }  
};  
```