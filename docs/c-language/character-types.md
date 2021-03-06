---
title: 字符类型 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cd26eea35da463211b144e98faa0636f5204f6f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="character-types"></a>字符类型
前面没有字母 L 的整数字符常量具有类型 `int`。 包含单个字符的整数字符常量的值是解释为整数的字符的数字值。 例如，字符 `a` 的数字值在十进制和十六进制下分别为 97 和 61。  
  
 从语法上来说，“宽字符常量”是带有字母 L 前缀的字符常量。宽字符常量具有类型 `wchar_t`（在 STDDEF.H 头文件中定义的整型）。 例如:  
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 宽字符常量的宽度为 16 位，用于指定扩展执行字符集的成员。 它们允许您用字母表示因太大而无法用类型 `char` 表示的字符。 有关宽字符的详细信息，请参阅[多字节和宽字符](../c-language/multibyte-and-wide-characters.md)。  
  
## <a name="see-also"></a>请参阅  
 [C 字符常量](../c-language/c-character-constants.md)