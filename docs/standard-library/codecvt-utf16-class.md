---
title: codecvt_utf16 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93113e64e9b6a72f40557d063f83724c5ff8da62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="codecvtutf16"></a>codecvt_utf16

表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 或 UTF-16BE 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>参数

`Elem` 宽字符元素类型。
`Maxcode` 最大的区域设置 facet 的字符数。
`Mode` 区域设置 facet 的配置信息。

## <a name="remarks"></a>备注

此模板类在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 的字节流之间转换，编码为 Mode 和 little_endian 或 UTF-16BE 则除外。

字节流应写入二进制文件；如果写入文本文件，则可能会损坏。

## <a name="requirements"></a>要求

标头：\<codecvt> Namespace: std