---
title: 如何： 实现 C# 的 lock 关键字 (C + + /cli CLI) |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lock statement
- lock C# keyword [C++]
ms.assetid: 436fe544-ffb7-49b9-9798-90794e9974de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dba651a7bcbfb1e8d7a0d107fe2400e222b06111
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-the-lock-c-keyword-ccli"></a>如何：实现 C# 的 lock 关键字 (C++/CLI)
本主题演示如何实现的 C# `lock` Visual c + + 中的关键字。 
  
 你还可以使用`lock`c + + 支持库中的类。 请参阅[同步 (lock 类)](../dotnet/synchronization-lock-class.md)有关详细信息。  
  
## <a name="example"></a>示例  
  
```  
// CS_lock_in_CPP.cpp  
// compile with: /clr  
using namespace System::Threading;  
ref class Lock {  
   Object^ m_pObject;  
public:  
   Lock( Object ^ pObject ) : m_pObject( pObject ) {  
      Monitor::Enter( m_pObject );  
   }  
   ~Lock() {  
      Monitor::Exit( m_pObject );  
   }  
};  
  
ref struct LockHelper {  
   void DoSomething();  
};  
  
void LockHelper::DoSomething() {  
   // Note: Reference type with stack allocation semantics to provide   
   // deterministic finalization  
  
   Lock lock( this );     
   // LockHelper instance is locked  
}  
  
int main()  
{  
   LockHelper lockHelper;  
   lockHelper.DoSomething();  
   return 0;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [与其他 .NET 语言的互操作性 (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)