---
title: _ATL_BASE_MODULE70 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b4e0173ecca5256ed942c23dbaf377850ee8192
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 结构
使用 atl。 任何项目使用  
  
## <a name="syntax"></a>语法  
  
```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```  
  
## <a name="members"></a>成员  
 `cbSize`  
 结构，用于版本控制的大小。  
  
 `m_hInst`  
 **HInstance**为此模块 （exe 或 dll）。  
  
 `m_hInstResource`  
 默认实例资源句柄。  
  
 **m_bNT5orWin98**  
 操作系统版本信息。 Atl。 在内部使用  
  
 **dwAtlBuildVer**  
 将存储的新版 atl。 当前 0x0700。  
  
 **pguidVer**  
 ATL 的内部 GUID。  
  
 **m_csResource**  
 使用对访问进行同步**m_rgResourceInstance**数组。 Atl。 在内部使用  
  
 **m_rgResourceInstance**  
 用于搜索 ATL 的感知的所有资源实例中的资源的数组。 Atl。 在内部使用  
  
## <a name="remarks"></a>备注  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)指的 typedef `_ATL_BASE_MODULE70`。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcore.h  
  
## <a name="see-also"></a>请参阅  
 [结构](../../atl/reference/atl-structures.md)





