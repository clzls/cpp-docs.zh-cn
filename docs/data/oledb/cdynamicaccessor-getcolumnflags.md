---
title: 'Cdynamicaccessor:: Getcolumnflags |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- GetColumnFlags
dev_langs:
- C++
helpviewer_keywords:
- GetColumnFlags method
ms.assetid: b2ba2f3a-2c61-4a49-abfb-75823908ccf4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9cb4e439ab650793dcbafa79092d03b53271e45a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetcolumnflags"></a>CDynamicAccessor::GetColumnFlags
检索列特征。  
  
## <a name="syntax"></a>语法  
  
```
bool GetColumnFlags(DBORDINAL nColumn,   
  DBCOLUMNFLAGS* pFlags) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nColumn`  
 [in] 列号。 列编号从 1 开始。 值为 0 引用的书签列中，如果有的话。  
  
 `pFlags`  
 [out]指向描述列的特征的位掩码的指针。 请参阅中的"DBCOLUMNFLAGS 枚举类型" [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 返回**true**如果成功检索的列特征。 否则，返回 **false**。  
  
## <a name="remarks"></a>备注  
 从一个偏移的列号。 列零是一种特殊情况;如果可用，则书签。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)