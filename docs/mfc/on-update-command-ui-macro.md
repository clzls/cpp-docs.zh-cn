---
title: ON_UPDATE_COMMAND_UI 宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_UPDATE_COMMAND_UI
dev_langs:
- C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 726eba2edbb857784a3a23ddcfb2d69fd8e30a72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI 宏
使用**属性**窗口，以将用户界面对象连接到命令目标对象中的命令更新处理程序。 它会自动将用户界面对象的 ID 连接到 `ON_UPDATE_COMMAND_UI` 宏，并在对象中创建一个将处理更新的处理程序。 请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)有关详细信息。  
  
 例如，若要更新程序的编辑菜单中的全部清除命令，使用**属性**调用窗口在所选的类的命令更新处理程序函数声明中添加一个消息映射条目`OnUpdateEditClearAll`类中声明和一个空白函数模板类的实现文件中。 函数原型类似于这样：  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]  
  
 如所有处理程序，该函数将显示**afx_msg**关键字。 与所有更新处理程序一样，它采用一个参数（一个指向 `CCmdUI` 对象的指针）。  
  
## <a name="see-also"></a>请参阅  
 [如何：更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)

