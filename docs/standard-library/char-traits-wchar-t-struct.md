---
title: char_traits&lt;wchar_t&gt; 结构 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a117a7f9299591d971ecbfdd0a681b008937da33
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 结构

此类是模板结构 **char_traits\<CharType>** 对 `wchar_t` 类型的一个元素的专用化。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>备注

专用化允许结构利用库函数处理此 `wchar_t` 类型的对象。

## <a name="requirements"></a>要求

**标头：** \<string>

**命名空间：** std

## <a name="see-also"></a>请参阅

[char_traits 结构](../standard-library/char-traits-struct.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
