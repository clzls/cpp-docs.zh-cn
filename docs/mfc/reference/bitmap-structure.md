---
title: 位图结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa8bb4ab914b4e05eb21cfc45a243328d32bb6d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="bitmap-structure"></a>BITMAP 结构
**位图**结构定义的高度、 宽度、 颜色格式和逻辑位图的位值**。**  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagBITMAP {  /* bm */  
    int bmType;  
    int bmWidth;  
    int bmHeight;  
    int bmWidthBytes;  
    BYTE bmPlanes;  
    BYTE bmBitsPixel;  
    LPVOID bmBits;  
} BITMAP;  
```  
  
#### <a name="parameters"></a>参数  
 *bmType*  
 指定位图类型。 对于逻辑位图，此成员必须为 0。  
  
 *bmWidth*  
 指定位图的宽度（以像素为单位）。 此宽度必须大于 0。  
  
 *bmHeight*  
 指定位图的高度（以光栅行为单位）。 此高度必须大于 0。  
  
 *bmWidthBytes*  
 指定每个光栅行中的字节数。 此值必须是偶数，因为图形设备接口 (GDI) 假定位图的位值构成了整数（2 字节）值的数组。 换而言之， **bmWidthBytes** \* 8 必须是大于或等于时获取的值的 16 的下一个倍数**bmWidth**成员乘以**bmBitsPixel**成员。  
  
 *bmPlanes*  
 指定位图中的颜色平面的数量。  
  
 *bmBitsPixel*  
 指定每个平面上的定义像素所需的相邻颜色位的数量。  
  
 *bmBits*  
 指向位图的位值的位置。 **BmBits**成员必须是指向 1 字节值数组的长指针。  
  
## <a name="remarks"></a>备注  
 当前使用的位图格式是单色和彩色。 单色位图使用 1 位 1 平面格式。 每个扫描是 16 位的倍数。  
  
 扫描高度的单色位图组织方式如下*n*:  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 单色设备的像素是黑色或白色。 如果位图中的对应位是 1，则打开像素（白色）。 如果位图中的对应位是 0，则关闭像素（黑色）。  
  
 所有设备都支持位图**RC_BITBLT**中设置位**RASTERCAPS**索引[CDC::GetDeviceCaps](../../mfc/reference/cdc-class.md#getdevicecaps)成员函数。  
  
 每台设备都具有自己的唯一颜色格式。 为了将位图从一台设备传输到另一个，使用[GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879)和[SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) Windows 函数。  
  
## <a name="requirements"></a>要求  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
