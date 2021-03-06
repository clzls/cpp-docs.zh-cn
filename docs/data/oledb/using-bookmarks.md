---
title: 使用书签 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5aa16d5f2a3a02d0e9fd6bb3dd5de71494e81d4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-bookmarks"></a>使用书签
打开行集之前，你必须告知提供程序，你想要使用书签。 若要执行此操作，将设置**DBPROP_BOOKMARKS**属性**true**你属性中设置。 提供程序作为列零，检索书签，因此你必须使用特殊宏`BOOKMARK_ENTRY`和`CBookmark`类如果你使用的静态的访问器。 `CBookmark` 是一种模板类，其中的参数是书签缓冲区的长度以字节为单位。 所需的书签缓冲区的长度取决于提供程序。 如果你使用 ODBC OLE DB 提供程序，如下面的示例中所示，缓冲区必须是 4 个字节。  
  
```  
class CProducts  
{  
public:  
   CBookmark<4>   bookmark;  
  
   BEGIN_COLUMN_MAP(CProducts)  
      BOOKMARK_ENTRY(bookmark)  
   END_COLUMN_MAP()  
};  
  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_BOOKMARKS, true);  
  

CTable<CAccessor<CProducts>> product;  
product.Open(session, "Products", &propset);  
```  
  
 如果你使用`CDynamicAccessor`，在运行时动态分配的缓冲区。 在这种情况下，你可以使用的专用的版本`CBookmark`你不指定缓冲区的长度。 使用函数`GetBookmark`从当前记录时，检索书签，在此代码示例所示：  
  
```  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  

propset.AddProperty(DBPROP_BOOKMARKS, true);  

product.Open(session, "Products", &propset);  

product.MoveNext();  

product.GetBookmark(&bookmark);  
```  
  
 在提供程序中支持书签有关的信息，请参阅[用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)