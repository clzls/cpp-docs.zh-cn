---
title: 编译器错误 C2415 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ad06cdf891c9b958f6cf08e724f4003a8507c2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2415"></a>编译器错误 C2415
操作数类型不正确  
  
 操作码不使用此类型的操作数。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  操作码不支持的使用的操作数的数目。 检查程序集语言参考手册 》 来确定的正确数目的操作数。  
  
2.  较新的处理器支持与其他类型的指令。 调整[/arch （最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)选项以使用更高版本的处理器。