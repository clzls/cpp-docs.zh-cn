---
title: is_trivially_default_constructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f2bd65fa7145325fd4c5c2f1a2483851d0738b7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible 类

测试类型是否具有普通默认构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>参数

`Ty` 查询的类型。

## <a name="remarks"></a>备注

如果类型 `Ty` 是具有普通构造函数的类，则类型谓词的实例为 true；否则为 false。

类 `Ty` 的默认构造函数为普通构造函数，如果：

- 它是一个隐式声明的默认构造函数

- 类 `Ty` 没有虚函数

- 类 `Ty` 没有虚拟基

- 类 `Ty` 的所有直接基均具有普通构造函数

- 类类型的所有非静态数据成员的类具有普通构造函数

- 类的类型数组的所有非静态数据成员的类具有普通构造函数

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
