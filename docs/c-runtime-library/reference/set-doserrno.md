---
title: _set_doserrno | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_doserrno
- set_doserrno
dev_langs:
- C++
helpviewer_keywords:
- _set_doserrno function
- doserrno global variable
- set_doserrno function
- _doserrno global variable
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb3a8e7503ae27177fded4ff240bbf5ec5a670e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="setdoserrno"></a>_set_doserrno

设置 [_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 全局变量的值。

## <a name="syntax"></a>语法

```C
errno_t _set_doserrno( int error_value );
```

### <a name="parameters"></a>参数

*error_value*<br/>
新值 **_doserrno**。

## <a name="return-value"></a>返回值

如果成功，则返回 0。

## <a name="remarks"></a>备注

可能的值是在 Errno.h 中定义的。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_set_doserrno**|\<stdlib.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_get_doserrno](get-doserrno.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
