---
title: 'Cdberrorinfo:: Geterrorinfo |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 234e1f02-c307-4666-b3ce-2a4d62407fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5dc2e45c4ff1fa867c2687d4a7104a15bcda4508
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdberrorinfogeterrorinfo"></a>CDBErrorInfo::GetErrorInfo
调用[ierrorrecords:: Geterrorinfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)返回[IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx)到指定的记录的接口指针。  
  
## <a name="syntax"></a>语法  
  
```
HRESULT GetErrorInfo(ULONG ulRecordNum,   
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ierrorrecords:: Geterrorinfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)