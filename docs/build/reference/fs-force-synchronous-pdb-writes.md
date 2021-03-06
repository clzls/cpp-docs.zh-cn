---
title: -FS （强制同步 PDB 写入） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FS
dev_langs:
- C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8565022a77742a1a8c7ed1f243a192d94c8627fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS（强制同步 PDB 写入）
强制写入到程序数据库 (PDB) 文件-由[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)或[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)— 通过 MSPDBSRV 进行序列化。EXE。  
  
## <a name="syntax"></a>语法  
  
```  
/FS  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，当 **/Zi**或 **/ZI**指定，编译器将锁定 PDB 文件以写入类型信息和符号化调试信息。 当类型的数目很大时，这可以显著缩短编译器生成类型信息的时间。 如果另一个进程（例如某个防病毒程序）临时锁定了 PDB 文件，则编译器的写入可能失败并可能产生错误。 当 cl.exe 的多个副本访问同一 PDB 文件时，此问题也可能发生。例如，如果您的解决方案具有使用相同的中间目录或输出目录并启用了并行生成的独立项目。 **/FS**编译器选项可阻止编译器锁定 PDB 文件，并强制写入要通过 MSPDBSRV。EXE，序列化访问。 这可能极大延长生成的时间，并且它无法阻止可能在 cl.exe 的多个实例同时访问 PDB 文件时发生的错误。 建议您更改解决方案，以便让独立项目对单独的中间文件和输出位置进行写入，或者您也可以使其中一个项目依赖于另一个项目来强制序列化项目生成。  
  
 [/MP](../../build/reference/mp-build-with-multiple-processes.md)选项使 **/FS**默认情况下。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +** 文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  修改**其他选项**属性以包含`/FS`，然后选择**确定**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)