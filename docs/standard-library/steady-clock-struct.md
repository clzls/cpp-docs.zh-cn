---
title: steady_clock 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1dbfac1eb8c67c5306bded6e6fd9ee8dacf54b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="steadyclock-struct"></a>steady_clock 结构

表示 `steady` 时钟。

## <a name="syntax"></a>语法

```cpp
struct steady_clock;
```

## <a name="remarks"></a>备注

在 Windows 上，steady_clock 会包装 QueryPerformanceCounter 函数。

如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为单调时钟。

如果它是单调时钟并且时钟计时周期之间的时间是常量，则为稳定时钟。

High_resolution_clock 是 steady_clock 的 typdef。

## <a name="public-functions"></a>公共函数

|函数|描述|
|--------------|-----------------|
|现在|返回当前时间作为 time_point 值。|

## <a name="public-constants"></a>公共常量

|名称|描述|
|----------|-----------------|
|`system_clock::is_steady`|保存 `true`。 `steady_clock` 是*稳定的*。|

## <a name="requirements"></a>要求

**标头：** \<chrono >

**命名空间：**std::chrono

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[system_clock 结构](../standard-library/system-clock-structure.md)<br/>
