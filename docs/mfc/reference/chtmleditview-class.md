---
title: CHtmlEditView 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10f474ce860bf5d9071a93f17654123f4777efa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="chtmleditview-class"></a>CHtmlEditView 类
提供 MFC 文档/视图体系结构上下文中的 Web 浏览器编辑平台功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|构造 `CHtmlEditView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHtmlEditView::Create](#create)|创建一个新的窗口对象。|  
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|返回**IHTMLDocument2**当前文档上的接口。|  
|[CHtmlEditView::GetStartDocument](#getstartdocument)|检索默认文档的此视图的名称。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## <a name="requirements"></a>要求  
 **标头：** afxhtml.h  
  
##  <a name="chtmleditview"></a>  CHtmlEditView::CHtmlEditView  
 构造 `CHtmlEditView` 对象。  
  
```  
CHtmlEditView();
```  
  
##  <a name="create"></a>  CHtmlEditView::Create  
 创建一个新的窗口对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszClassName`  
 指向以 null 结尾的字符串名称的 Windows 类。 类名称可以是与注册的任何名称[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数或**RegisterClass** Windows 函数。 如果**NULL**，使用预定义的默认[CFrameWnd](../../mfc/reference/cframewnd-class.md)属性。  
  
 `lpszWindowName`  
 指向以 null 结尾的字符串表示的窗口名称。  
  
 `dwStyle`  
 指定的窗口样式特性。 默认情况下， **WS_VISIBLE**和**WS_CHILD**设置窗口样式。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定的大小和窗口的位置。 `rectDefault`值允许 Windows 指定的大小和位置的新窗口。  
  
 `pParentWnd`  
 指向控件的父窗口的指针。  
  
 `nID`  
 视图的 ID 号。 默认情况下，设置为**AFX_IDW_PANE_FIRST**。  
  
 `pContext`  
 指向的指针[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)。 **NULL**默认情况下。  
  
### <a name="remarks"></a>备注  
 此方法还将调用包含的 WebBrowser**导航**方法以加载默认文档 (请参阅[CHtmlEditView::GetStartDocument](#getstartdocument))。  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument  
 返回**IHTMLDocument2**当前文档上的接口。  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>参数  
 `ppDocument`  
 [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)接口。  
  
##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument  
 检索默认文档的此视图的名称。  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>请参阅  
 [HTMLEdit 示例](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


