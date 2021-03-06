---
title: 增强简单的只读提供程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c88714e4e1651839cdc5fd4b92d3c5222aa08d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="enhancing-the-simple-read-only-provider"></a>增强简单的只读提供程序
本部分说明如何增强[简单只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)在上一节中创建。 `IRowsetLocateImpl` 创建的实现`IRowsetLocate`接口，并添加了对你的书签支持。  
  
 在工作提供商，你可能想要增强以使提供程序更新，处理事务，或增强的行提取算法的性能。 大多数提供程序增强涉及将接口添加到现有的 COM 对象。  
  
 以下主题中的示例通过添加增强的行提取的机制`IRowsetLocate`接口`CAgentRowset`。 主题介绍了如何为：  
  
-   [请从 IRowsetLocate 继承 RMyProviderRowset](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md)。  
  
-   [动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>请参阅  
 [创建简单的只读提供程序](../../data/oledb/creating-a-simple-read-only-provider.md)