---
title: hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _hypotf
- hypot
- hypotf
- _hypot
- _hypotl
- hypotl
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
- hypotf
- hypotl
- _hypotl
- hypot
- _hypot
- _hypotf
dev_langs:
- C++
helpviewer_keywords:
- hypotenuse calculation
- hypot function
- hypotf function
- triangles, calculating hypotenuse
- hypotl function
- calculating hypotenuses
- _hypot function
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a8488b160c10eb29f0448127c44d3514f8debf3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="hypot-hypotf-hypotl-hypot-hypotf-hypotl"></a>hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl

计算斜边。

## <a name="syntax"></a>语法

```C
double hypot(
   double x,
   double y
);
float hypotf(
   float x,
   float y
);
long double hypotl(
   long double x,
   long double y
);
double _hypot(
   double x,
   double y
);
float _hypotf(
   float x,
   float y
);
long double _hypotl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>参数

*x*， *y*<br/>
浮点值。

## <a name="return-value"></a>返回值

如果成功， **hypot**返回长度的斜边; 在溢出时， **hypot**返回 INF （无穷大） 和**errno**变量设置为**ERANGE**. 你可以使用 **_matherr**来修改错误处理。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Hypot**函数计算直角三角形，给定两条边的长度的斜边长度*x*和*y* （换而言之，平方根*x*<sup>2</sup> + *y*<sup>2</sup>)。

提供的带有前导下划线的函数版本便于与早期的标准兼容。 它们的行为与没有前导下划线的版本相同。 我们建议将不带前导下划线的版本用于新代码。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**hypot**， **hypotf**， **hypotl**， **_hypot**， **_hypotf**， **_hypotl**|\<math.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_hypot.c
// This program prints the hypotenuse of a right triangle.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 3.0, y = 4.0;

   printf( "If a right triangle has sides %2.1f and %2.1f, "
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );
}
```

```Output
If a right triangle has sides 3.0 and 4.0, its hypotenuse is 5.0
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[_matherr](matherr.md)<br/>