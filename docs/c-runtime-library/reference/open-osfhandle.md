---
title: _open_osfhandle | Microsoft 文档
ms.custom: ''
ms.date: 12/12/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: beb8c074beeb47274fbae21ea293d0ea55f28d36
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="openosfhandle"></a>_open_osfhandle

将 C 运行时文件描述符与现有操作系统文件句柄关联。

## <a name="syntax"></a>语法

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>参数

*osfhandle*<br/>
操作系统文件句柄。

*flags*<br/>
允许的操作类型。

## <a name="return-value"></a>返回值

如果成功， **_open_osfhandle**返回 C 运行时文件描述符。 否则，它将返回-1。

## <a name="remarks"></a>备注

**_Open_osfhandle**函数分配的 C 运行时文件描述符，并将其与指定的操作系统文件句柄关联*osfhandle*。 *标志*自变量是由一个或多个 Fcntl.h 中定义的清单常量构成一个整数表达式。 当两个或多个清单常量来形成*标志*自变量，这些常量将与按位 OR 运算符合并 ( **&#124;** )。

Fcntl.h 中定义的以下清单常量：

**\_O\_追加**定位文件指针到每个写入操作之前的文件的末尾。

**\_O\_RDONLY**打开只读文件。

**\_O\_文本**在文本 （转换） 模式下打开该文件。

**\_O\_WTEXT**在 Unicode (已翻译 utf-16) 模式下打开该文件。

要关闭使用打开的文件 **_open_osfhandle**，调用[\_关闭](close.md)。 通过调用也关闭基础的操作系统文件句柄 **_close**，因此不需要调用 Win32 函数**CloseHandle**对原始句柄。 如果由所拥有的文件描述符**文件&#42;** 流，然后调用[fclose](fclose-fcloseall.md)上**文件&#42;** 流也会关闭这两个的文件描述符与基础句柄。 在这种情况下，不要调用 **_close**上的文件描述符。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
