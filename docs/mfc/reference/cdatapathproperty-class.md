---
title: CDataPathProperty 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2559b4917f16bb8ddc49b73ace8bda6e1a9bafc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty 类
实现可异步加载的 OLE 控件属性。  
  
## <a name="syntax"></a>语法  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|构造 `CDataPathProperty` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|检索与关联的异步 OLE 控件`CDataPathProperty`对象。|  
|[CDataPathProperty::GetPath](#getpath)|检索的属性的路径名。|  
|[CDataPathProperty::Open](#open)|启动加载关联 ActiveX (OLE) 控件的异步属性。|  
|[CDataPathProperty::ResetData](#resetdata)|调用`CAsyncMonikerFile::OnDataAvailable`以通知容器的控件属性已更改。|  
|[CDataPathProperty::SetControl](#setcontrol)|设置与属性关联的异步 ActiveX (OLE) 控件。|  
|[CDataPathProperty::SetPath](#setpath)|设置属性的路径名。|  
  
## <a name="remarks"></a>备注  
 可以在同步启动之后加载异步属性。  
  
 类`CDataPathProperty`派生自**CAysncMonikerFile**。 若要在 OLE 控件中实现异步属性，从派生类`CDataPathProperty`，并重写[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。  
  
 有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息，请参阅以下文章：  
  
- [Internet 前几个步骤： ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet 前几个步骤： 异步名字对象](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>要求  
 **标头：** afxctl.h  
  
##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty  
 构造 `CDataPathProperty` 对象。  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 指向 OLE 控件对象要与此相关联的`CDataPathProperty`对象。  
  
 `lpszPath`  
 路径，这可能是绝对或相对，用于创建异步名字对象引用的属性的实际绝对位置。 `CDataPathProperty` 使用 Url，不是文件名。 如果你想`CDataPathProperty`对象文件中，前面预置`file://`到路径。  
  
### <a name="remarks"></a>备注  
 `COleControl`指向对象`pControl`由**打开**和检索由派生类。 如果`pControl`是**NULL**，与所使用的控件**打开**应与设置`SetControl`。 如果`lpszPath`是**NULL**，可以在路径中，通过传递**打开**或将其与设置`SetPath`。  
  
##  <a name="getcontrol"></a>  CDataPathProperty::GetControl  
 调用此成员函数可检索`COleControl`与关联的对象`CDataPathProperty`对象。  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>返回值  
 返回指向 OLE 控件的指针与关联`CDataPathProperty`对象。 **NULL**如果不控件关联。  
  
##  <a name="getpath"></a>  CDataPathProperty::GetPath  
 调用此成员函数可检索的路径、 时设置`CDataPathProperty`对象已构造的或在指定**打开**，或对上一个调用中指定`SetPath`成员函数。  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回于属性自身的路径名。 如果可以为空指定没有路径。  
  
##  <a name="open"></a>  CDataPathProperty::Open  
 调用此成员函数可启动的关联控件的异步属性加载。  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 指向 OLE 控件对象要与此相关联的`CDataPathProperty`对象。  
  
 `pError`  
 指向文件异常的指针。 发生错误时将设置的原因。  
  
 `lpszPath`  
 路径，这可能是绝对或相对，用于创建异步名字对象引用的属性的实际绝对位置。 `CDataPathProperty` 使用 Url，不是文件名。 如果你想`CDataPathProperty`对象文件中，前面预置`file://`到路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该函数尝试获取`IBindHost`从控件的接口。  
  
 之前调用**打开**如果没有路径，该属性的路径的值必须设置。 这可以对对象进行构造，或通过调用时`SetPath`成员函数。  
  
 之前调用**打开**不会进行控制，ActiveX 控件 （以前称为 OLE 控件） 可以是与对象关联。 进行这种对象时构造，或通过调用`SetControl`。  
  
 所有重载[CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open)还可以从中`CDataPathProperty`。  
  
##  <a name="resetdata"></a>  CDataPathProperty::ResetData  
 调用此函数可获取`CAsyncMonikerFile::OnDataAvailable`以通知容器的控件属性已发生更改，并以异步方式加载的所有信息都都不再有用。  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>备注  
 打开应重新启动。 派生的类可以重写此函数以使用不同的默认值。  
  
##  <a name="setcontrol"></a>  CDataPathProperty::SetControl  
 调用此成员函数可将具有的异步 OLE 控件相关联`CDataPathProperty`对象。  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 指向要与属性关联的异步 OLE 控件的指针。  
  
##  <a name="setpath"></a>  CDataPathProperty::SetPath  
 调用此成员函数可设置的属性的路径名。  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>参数  
 `lpszPath`  
 路径，这可能是绝对或相对，异步加载的属性。 `CDataPathProperty` 使用 Url，不是文件名。 如果你想`CDataPathProperty`对象文件中，前面预置`file://`到路径。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例图像](../../visual-cpp-samples.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)
