---
title: ISpecifyPropertyPagesImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74f10684c32cc5b1b4b07ac30406520c9ba41ddd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl 类
此类实现**IUnknown**并提供的默认实现[ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217)接口。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`ISpecifyPropertyPagesImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|填充的 UUID 计数数组值。 每个 UUID 对应于一个可以显示对象的属性表中的属性页的 CLSID。|  
  
## <a name="remarks"></a>备注  
 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217)接口允许客户端获取有关支持的对象的属性页的 Clsid 的列表。 类`ISpecifyPropertyPagesImpl`提供默认实现此接口并实现**IUnknown**信息发送给转储设备在调试生成。  
  
> [!NOTE]
>  不会公开**ISpecifyPropertyPages**接口如果你的对象不支持属性页。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages  
 在填充数组[CAUUID](http://msdn.microsoft.com/library/windows/desktop/ms680048)结构可以显示对象的属性表中的属性页的 Clsid。  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来检索每个 CLSID。  
  
 请参阅[ISpecifyPropertyPages::GetPages](http://msdn.microsoft.com/library/windows/desktop/ms687276) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)   
 [IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)
