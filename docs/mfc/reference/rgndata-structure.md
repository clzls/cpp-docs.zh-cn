---
title: RGNDATA 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- RGNDATA
dev_langs:
- C++
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 591c2dd65fdb9dde00f0ac1373c39affbe82da85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="rgndata-structure"></a>RGNDATA 结构
`RGNDATA` 结构包含一个标头和构成区域的矩形的数组。 这些矩形的顺序为从上到下、从左到右，不会重叠。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _RGNDATA { /* rgnd */  
    RGNDATAHEADER rdh;  
    char Buffer[1];  
} RGNDATA;  
```  
  
#### <a name="parameters"></a>参数  
 *rdh*  
 指定[RGNDATAHEADER](http://msdn.microsoft.com/library/windows/desktop/dd162941)结构。 （有关此结构的详细信息，请参阅 Windows SDK）。此结构的成员指定区域的类型（区域是矩形还是梯形）、组成区域的矩形数量、包含矩形结构的缓冲区的大小等。  
  
 `Buffer`  
 指定包含任意大小的缓冲区[RECT](../../mfc/reference/rect-structure1.md)组成区域的结构。  
  
## <a name="requirements"></a>要求  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

