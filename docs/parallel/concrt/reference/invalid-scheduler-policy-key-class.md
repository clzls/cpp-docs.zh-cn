---
title: invalid_scheduler_policy_key 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78bc955b43f3b6650f7a2fe654e5920c9cac971
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key 类
此类描述无效或未知键传递给 `SchedulerPolicy` 对象构造函数，或 `SchedulerPolicy` 对象的 `SetPolicyValue` 方法被传递了必须使用其他方式（例如 `SetConcurrencyLimits` 方法）进行更改的键时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class invalid_scheduler_policy_key : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[invalid_scheduler_policy_key](#ctor)|已重载。 构造 `invalid_scheduler_policy_key` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> invalid_scheduler_policy_key 

 构造 `invalid_scheduler_policy_key` 对象。  
  
```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [SchedulerPolicy 类](schedulerpolicy-class.md)
