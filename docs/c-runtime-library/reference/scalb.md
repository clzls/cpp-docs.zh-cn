---
title: _scalb，_scalbf |Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _scalb
- _scalbf
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- scalb
- _scalb
- _scalbf
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a465ca74af72a5114eac949439ab8493f89bcb39
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="scalb-scalbf"></a>_scalb _scalbf

按 2 的幂缩放自变量。

## <a name="syntax"></a>语法

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>参数

*x*<br/>
双精度浮点值。

*exp*<br/>
长整数指数。

## <a name="return-value"></a>返回值

如果成功，则返回指数值。 在溢出 (具体取决于的符号*x*)， **_scalb**返回 + /- **HUGE_VAL**; **errno**变量设置为**ERANGE**。

有关此代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Scalb**函数计算的值*x* * 2<sup>*exp*</sup>。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_scalb**， **_scalbf**|\<float.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
