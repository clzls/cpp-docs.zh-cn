---
title: strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
dev_langs:
- C++
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4be0a1179f5b3195d5fafbaf679311c0dcf9edd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l

根据区域设置特定信息转换字符串。

## <a name="syntax"></a>语法

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strDest*<br/>
目标字符串。

*strSource*<br/>
源字符串。

*count*<br/>
最大字符将放入数*strDest*。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回转换的字符串的长度（不算结尾的 null 字符）。 返回的值是否大于或等于*计数*，则内容的*strDest*是不可预知的。 发生错误时，每个函数设置**errno**并返回**INT_MAX**。 对于无效字符， **errno**设置为**EILSEQ**。

## <a name="remarks"></a>备注

**Strxfrm**指向的字符串转换函数*strSource*到新的排序格式存储在*strDest*。 不能超过*计数*个字符，包括 null 字符，进行转换并放入到结果字符串。 使用的区域设置进行转换**LC_COLLATE**类设置。 有关详细信息**LC_COLLATE**，请参阅[setlocale](setlocale-wsetlocale.md)。 **strxfrm**使用当前区域设置为其区域设置相关的行为;**_strxfrm_l**是相同，只不过它使用而不是当前区域设置中传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

转换完成之后，调用**strcmp**使用两个已转换字符串生成的结果相同的调用**strcoll**应用于原始的两个字符串。 与**strcoll**和**stricoll**， **strxfrm**自动处理根据多字节字符字符串。

**wcsxfrm**是宽字符版本的**strxfrm**; 的字符串自变量**wcsxfrm**都是宽字符指针。 有关**wcsxfrm**之后，在字符串转换，调用**wcscmp**使用两个已转换字符串生成的结果相同的调用**wcscoll**应用于原始的两个字符串。 **wcsxfrm**和**strxfrm**否则具有相同行为。 **wcsxfrm**使用当前区域设置为其区域设置相关的行为;**_wcsxfrm_l**而不是当前区域设置中传入的区域设置。

这些函数验证其参数。 如果*strSource*是 null 指针，或*strDest* （除非计数为零） 为 NULL 指针，或如果*计数*大于**INT_MAX**，调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**INT_MAX**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

在“C”区域设置中，字符集（ASCII 字符集）中的字符顺序与字典中的字符顺序相同。 但是在其他区域设置中，字符集中的字符顺序可能与字典中的字符顺序不同。 例如，在某些欧洲区域设置中，字符集中的字符“a”（值 0x61）位于字符“&\#x00E4;”（值 0xE4）之前，但在字典顺序中字符“ä”位于字符“a”之前。

在为其字符集和字典字符顺序不同的区域设置，使用**strxfrm**对原始字符串，然后**strcmp**对结果字符串，以生成按字典顺序的字符串根据当前区域设置的比较**LC_COLLATE**类设置。 因此，若要比较两个字符串字典顺序中的上述的区域设置，请使用**strxfrm**对原始字符串，然后**strcmp**对结果字符串。 或者，可以使用**strcoll**而非**strcmp**对原始字符串。

**strxfrm**基本上是周围的包装器[LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700)与**LCMAP_SORTKEY**。

下面的表达式的值是包含所需的数组的大小**strxfrm**源字符串内的转换：

`1 + strxfrm( NULL, string, 0 )`

在"C"区域设置仅， **strxfrm**等效于以下：

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> 或 \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
