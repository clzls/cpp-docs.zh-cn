---
title: progress_reporter 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs:
- C++
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5d4dc98c4fb411a4d63fdfad5049cf0df723bec
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="progressreporter-class"></a>progress_reporter 类
进度报告器类允许报告特定类型的进度通知。 每个 progress_reporter 对象都是绑定到特定异步动作或操作的。  
  
## <a name="syntax"></a>语法  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>参数  
 `_ProgressType`  
 通过进度报告器报告的每个进度通知的负载类型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[report](#report)|向进度报告器绑定到的异步动作或操作发送进度报告。|  
  
## <a name="remarks"></a>备注  
 此类型是仅可用于 Windows 运行时应用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `progress_reporter`  
  
## <a name="requirements"></a>要求  
 **标头：** ppltasks.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> progress_reporter 

```
progress_reporter();
```  
  
##  <a name="report"></a> 报表 

 向进度报告器绑定到的异步动作或操作发送进度报告。  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>参数  
 `val`  
 报表通过进度通知负载。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
