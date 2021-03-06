---
title: NotifyHandler |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- NotifyHandler
dev_langs:
- C++
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74fbdd99c162b4362339d8c1b45ddc281d30eeee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="notifyhandler"></a>NotifyHandler
标识的第三个参数的函数的名称`NOTIFY_HANDLER`消息映射中的宏。  
  
## <a name="syntax"></a>语法  
  
```  
 
    LRESULT 
    NotifyHandler 
 (
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>参数  
 `idCtrl`  
 发送消息的控件的标识符。  
  
 *pnmh*  
 地址[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)包含通知代码以及其他信息的结构。 对于某些通知消息，此参数指向具有较大结构**NMHDR**结构用作其第一个成员。  
  
 `bHandled`  
 消息映射集`bHandled`到**TRUE**之前*NotifyHandler*调用。 如果*NotifyHandler*并不完全处理消息，它应设置`bHandled`到**FALSE**以指示消息需要进一步处理。  
  
## <a name="return-value"></a>返回值  
 消息处理的结果。 如果成功，则为 0。  
  
## <a name="remarks"></a>备注  
 有关消息映射中使用此消息处理程序的示例，请参阅[NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))。  
  
## <a name="see-also"></a>请参阅  
 [实现一个窗口](../atl/implementing-a-window.md)   
 [消息映射](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

