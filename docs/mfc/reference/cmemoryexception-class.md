---
title: CMemoryException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12971af6bed7c04c6f6f214f0b583a4f7e6eb7a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmemoryexception-class"></a>CMemoryException 类
表示内存不足异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](#cmemoryexception)|构造 `CMemoryException` 对象。|  
  
## <a name="remarks"></a>备注  
 没有进一步限定是必要或不可能。 自动引发内存异常**新**。 如果您编写您自己的内存函数，则使用`malloc`，对于示例中，则你将负责引发内存异常。  
  
 有关详细信息`CMemoryException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException  
 构造 `CMemoryException` 对象。  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>备注  
 不直接，使用此构造函数，但而是调用全局函数[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 此全局函数可以在内存不足的情况下成功，因为它构造之前分配的内存中的异常对象。 有关异常处理的详细信息，请参阅文章[异常](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [CException 类](cexception-class.md)   
 [层次结构图](../hierarchy-chart.md)



