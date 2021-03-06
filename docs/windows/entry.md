---
title: 条目 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db90390be5313ddbea1103105f47b55fe9e23d62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="entry"></a>entry
通过标识 DLL 中的入口点，在模块中指定导出的函数或常量。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 `id`  
 入口点的 ID。  
  
## <a name="remarks"></a>备注  
 **条目**c + + 属性具有相同的功能[条目](http://msdn.microsoft.com/library/windows/desktop/aa366815)MIDL 特性。  
  
## <a name="example"></a>示例  
 请参阅示例[idl_module](../windows/idl-module.md)的示例使用**条目**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`idl_module` 特性|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
