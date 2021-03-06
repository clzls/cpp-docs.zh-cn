---
title: 更改符号或符号名 (ID) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols, names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 28d31fc27fdc51a3a5b05dba96ab9decf4fc7e00
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>更改符号或符号名 (ID)
创建新资源或资源对象时，开发环境会向它分配默认符号名，例如 IDD_DIALOG1。 你可以使用[属性窗口](/visualstudio/ide/reference/properties-window)更改默认符号名，或更改已与资源关联的任何符号的名称。  
  
### <a name="to-change-a-resources-symbol-name"></a>更改资源的符号名  
  
1.  在[资源视图](../windows/resource-view-window.md)，选择资源。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**属性**窗口中，键入新的符号名称，或从现有符号列表中选择**ID**框。  
  
     如果输入新符号名，则会自动向它赋值。  
  
 你可以使用[资源符号对话框](../windows/resource-symbols-dialog-box.md)若要更改的当前未分配给资源的符号的名称。 有关详细信息，请参阅[更改未分配的符号](../windows/changing-unassigned-symbols.md)。  
  

  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [符号名限制](../windows/symbol-name-restrictions.md)   
 [预定义的符号 ID](../windows/predefined-symbol-ids.md)