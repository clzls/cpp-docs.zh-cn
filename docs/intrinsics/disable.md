---
title: _disable |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _disable_cpp
- _disable
dev_langs:
- C++
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4359d77f13338e2e007236b0103fd358dffd0ce1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="disable"></a>_disable
**Microsoft 专用**  
  
 禁用中断。  
  
## <a name="syntax"></a>语法  
  
```  
void _disable(void);  
```  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_disable`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 `_disable` 指示处理器去清除中断标记。 在 x86 系统上，此函数会生成“清除中断标记”(`cli`) 指令。  
  
 此函数只有在内核模式下才可用。 如果在用户模式下使用，运行时会出现特权指令异常。  
  
 在 ARM 平台上，此例程只能用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)