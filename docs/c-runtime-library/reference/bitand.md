---
title: bitand | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- std::bitand
- std.bitand
- bitand
dev_langs:
- C++
helpviewer_keywords:
- bitand function
ms.assetid: 279cf9b5-fac1-49de-b329-f1a31b3481fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f918608740960fef278c615d8f4b8b627a3e96f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="bitand"></a>bitand

& 运算符的替代项。

## <a name="syntax"></a>语法

```C

#define bitand &

```

## <a name="remarks"></a>备注

该宏产生运算符

## <a name="example"></a>示例

```cpp
// iso646_bitand.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 1, b = 2, result;

   result = a & b;
   cout << result << endl;

   result= a bitand b;
   cout << result << endl;
}
```

```Output
0
0
```

## <a name="requirements"></a>要求

**标头：** \<iso646.h>