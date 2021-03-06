---
title: bsearch | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- bsearch
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- bsearch
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77d7576b5e8914148a8c67d8df82573c1f379e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="bsearch"></a>bsearch

执行排序数组的二进制搜索。 提供此函数的一个更安全的版本，请参阅 [bsearch_s](bsearch-s.md)。

## <a name="syntax"></a>语法

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>参数

*key*<br/>
要搜索的对象。

*base*<br/>
指向搜索数据的基项的指针。

*数*<br/>
元素数量。

*width*<br/>
元素的宽度。

*compare*<br/>
比较两个元素的回调函数。 第一个是指向用于搜索的键的指针，第二个是指向将与该键进行比较的数组元素的指针。

## <a name="return-value"></a>返回值

**bsearch**将指针返回到的匹配项*密钥*指向数组中*基*。 如果*密钥*未找到，则该函数将返回**NULL**。 如果数组不是以升序排序的，或包含具有相同键的重复记录，则不可预知结果。

## <a name="remarks"></a>备注

**Bsearch**函数执行的已排序数组的二进制搜索*数*元素，每个*宽度*大小中的字节数。 *基*值是指向要搜索，该数组的基和*密钥*是正在查找的值。 *比较*参数是指向用户提供的例程将请求的键与数组元素进行比较并返回指定其关系的以下值之一：

|返回值*比较*例程|描述|
|-----------------------------------------|-----------------|
|\< 0|键小于数组元素。|
|0|键等于数组元素。|
|> 0|键大于数组元素。|

此函数验证其参数。 如果*比较*，*密钥*或*数*是**NULL**，或者如果*基*是**NULL**和 **数*不为零，或者如果*宽度*为零，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和该函数将返回**NULL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> 和 \<search.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序对具有 qsort 的字符串数组进行排序，然后使用 bsearch 查找单词“cat”。

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
