---
title: nonextensible |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87cdbf66676ed2a3e6054006270b39ad80325857
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="nonextensible"></a>nonextensible
指定`IDispatch`实现仅包括的属性和方法的接口描述中列出，并在运行时不能与其他成员扩展。  
  
## <a name="syntax"></a>语法  
  
```  
  
[nonextensible]  
  
```  
  
## <a name="remarks"></a>备注  
 **Nonextensible** c + + 属性具有相同的功能[nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) MIDL 特性。  
  
 利用**nonextensible**还要求[oleautomation](../windows/oleautomation.md)属性。  
  
## <a name="example"></a>示例  
 下面的代码演示一个使用**nonextensible**属性：  
  
```  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|否|  
|**必需的特性**|**双**和**oleautomation**，或**调度接口**|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
