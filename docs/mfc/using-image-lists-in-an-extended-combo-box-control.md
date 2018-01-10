---
title: "在扩展的组合框控件中使用图像列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ac69e7d0dbe1748a409b107579c747b7f9a4a7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>在扩展组合框控件中使用图像列表
扩展的组合框控件的主要功能是能够将映像从图像列表与组合框控件中的各个项相关联。 每个项都可以显示三个不同的映像： 一个用于其所选的状态，另一个用于其未选中的状态和第三个覆盖图像。  
  
 以下过程将图像列表与扩展的组合框控件相关联：  
  
### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>若要将图像列表与扩展的组合框控件相关联  
  
1.  构造一个新的图像列表 （或使用现有的图像列表对象），使用[CImageList](../mfc/reference/cimagelist-class.md)构造函数，并存储结果的指针。  
  
2.  通过调用中初始化新的图像列表对象[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下面的代码是此调用的一个示例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  添加为每个可能状态的可选图像： 所选或未选中，并覆盖。 以下代码添加三个预定义的映像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  与通过调用控件关联的图像列表[CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist)。  
  
 图像列表与控件关联后，你可以单独指定每个项将用于三种可能状态的映像。 有关详细信息，请参阅[设置单个项的图像](../mfc/setting-the-images-for-an-individual-item.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)
