---
title: CMemFile 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
dev_langs:
- C++
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81421c99623fd3ab0abde20b479ec1ba91c3f936
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmemfile-class"></a>CMemFile 类
[CFile](../../mfc/reference/cfile-class.md)-派生支持内存文件的类。  
  
## <a name="syntax"></a>语法  
  
```  
class CMemFile : public CFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMemFile::CMemFile](#cmemfile)|构造内存文件对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMemFile::Attach](#attach)|将附加到的内存块`CMemFile`。|  
|[CMemFile::Detach](#detach)|分离从的内存块`CMemFile`并返回到分离的内存块的指针。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMemFile::Alloc](#alloc)|重写以修改内存分配行为。|  
|[CMemFile::Free](#free)|重写以修改内存释放行为。|  
|[CMemFile::GrowFile](#growfile)|重写以修改增长文件时的行为。|  
|[CMemFile::Memcpy](#memcpy)|重写以修改内存复制行为时读取和写入文件。|  
|[CMemFile::Realloc](#realloc)|重写以修改内存重新分配行为。|  
  
## <a name="remarks"></a>备注  
 这些内存文件行为类似于磁盘文件，只不过该文件存储在 RAM 中，而不是在磁盘上。 内存文件可用于快速临时存储或传输原始字节或序列化的独立进程之间的对象。  
  
 `CMemFile` 对象可以自动分配其自己的内存，或者可以将附加到你自己内存块`CMemFile`对象通过调用[附加](#attach)。 在任一情况下，为自动增长的内存文件的内存分配中`nGrowBytes`-如果大小为增量`nGrowBytes`不为零。  
  
 内存块将自动删除在析构时`CMemFile`对象如果分配内存时最初通过`CMemFile`对象; 否则，你有责任释放附加到对象的内存。  
  
 你可以通过指针时您将其从分离提供访问的内存块`CMemFile`对象通过调用[分离](#detach)。  
  
 最常见的用途`CMemFile`是创建`CMemFile`对象并使用它通过调用[CFile](../../mfc/reference/cfile-class.md)成员函数。 请注意该创建`CMemFile`自动将其打开： 不调用[CFile::Open](../../mfc/reference/cfile-class.md#open)，其中仅使用磁盘文件。 因为`CMemFile`不使用磁盘文件，数据成员`CFile::m_hFile`未使用。  
  
 `CFile`成员函数[重复](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)未实现`CMemFile`。 如果你对调用这些函数`CMemFile`对象，则将会出现[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 `CMemFile` 使用运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)， [realloc](../../c-runtime-library/reference/realloc.md)，和[免费](../../c-runtime-library/reference/free.md)分配，重新分配和释放内存; 和内部函数[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)到块复制内存时读取和写入。 如果你想要更改此行为或行为时`CMemFile`会增大文件派生您自己的类从`CMemFile`和重写适当的函数。  
  
 有关详细信息`CMemFile`，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)和[内存管理 (MFC)](../../mfc/memory-management.md)并查看[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="alloc"></a>  CMemFile::Alloc  
 调用此函数`CMemFile`成员函数。  
  
```  
virtual BYTE* Alloc(SIZE_T nBytes);
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 要分配的内存的字节数。  
  
### <a name="return-value"></a>返回值  
 指向已分配的内存块的指针或**NULL**如果分配失败。  
  
### <a name="remarks"></a>备注  
 重写此函数可实现自定义的内存分配。 如果你重写此函数，你可能需要重写[免费](#free)和[Realloc](#realloc)以及。  
  
 默认实现使用运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)分配内存。  
  
##  <a name="attach"></a>  CMemFile::Attach  
 调用此函数可将附加到的内存块`CMemFile`。  
  
```  
void Attach(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpBuffer`  
 要附加到的缓冲区的指针`CMemFile`。  
  
 `nBufferSize`  
 一个整数，以字节为单位指定缓冲区的大小。  
  
 `nGrowBytes`  
 以字节为单位的内存分配增量。  
  
### <a name="remarks"></a>备注  
 这将导致`CMemFile`为内存文件中使用的内存块。  
  
 如果`nGrowBytes`为 0，`CMemFile`将设置为的文件长度`nBufferSize`。 这意味着，内存块中的数据之前已附加到`CMemFile`将用作该文件。 在这种方式中创建的内存文件无法增长。  
  
 因为该文件不能而增长，请注意，不会导致`CMemFile`尝试增大该文件。 例如，请勿调用`CMemFile`重写[CFile:Write](../../mfc/reference/cfile-class.md#write)到超过末尾写入或不调用[CFile:SetLength](../../mfc/reference/cfile-class.md#setlength)长度超过`nBufferSize`。  
  
 如果`nGrowBytes`大于 0，`CMemFile`将忽略已附加的内存块的内容。 你将需要的内存文件的内容写入从暂存使用`CMemFile`的重写`CFile::Write`。 如果你尝试写入文件的末尾，或通过调用增大文件`CMemFile`的重写`CFile::SetLength`，`CMemFile`将增长增量为内存分配`nGrowBytes`。 如果内存块将传递给不断增长的内存分配将失败**附加**未使用与兼容方法分配[Alloc](#alloc)。 若要使用的默认实现兼容`Alloc`，您必须分配内存，运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)或[calloc](../../c-runtime-library/reference/calloc.md)。  
  
##  <a name="cmemfile"></a>  CMemFile::CMemFile  
 第一个重载打开的空内存文件。  
  
```  
CMemFile(UINT nGrowBytes = 1024);

 
CMemFile(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>参数  
 `nGrowBytes`  
 以字节为单位的内存分配增量。  
  
 *lpBuffe*r  
 指向接收信息大小的缓冲区的指针`nBufferSize`。  
  
 `nBufferSize`  
 一个整数，以字节为单位指定文件缓冲区的大小。  
  
### <a name="remarks"></a>备注  
 请注意，构造函数打开该文件，并且你不应调用[CFile::Open](../../mfc/reference/cfile-class.md#open)。  
  
 第二个重载看起来相同，就像你使用第一个构造函数并立即调用[附加](#attach)使用相同的参数。 请参阅**附加**有关详细信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]  
  
##  <a name="detach"></a>  CMemFile::Detach  
 调用此函数可获取到正在使用的内存块的指针`CMemFile`。  
  
```  
BYTE* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向包含内存文件的内容的内存块的指针。  
  
### <a name="remarks"></a>备注  
 调用此函数还关闭`CMemFile`。 你可以重新附加到的内存块`CMemFile`通过调用[附加](#attach)。 如果你想要重新附加该文件并在其中使用的数据，则应调用[CFile::GetLength](../../mfc/reference/cfile-class.md#getlength)要获取之前调用文件长度**分离**。 请注意，如果附加到的内存块`CMemFile`，以便你可以使用其数据 ( `nGrowBytes` = = 0)，然后你将无法增长的内存文件。  
  
##  <a name="free"></a>  CMemFile::Free  
 调用此函数`CMemFile`成员函数。  
  
```  
virtual void Free(BYTE* lpMem);
```  
  
### <a name="parameters"></a>参数  
 `lpMem`  
 指向要释放的内存的指针。  
  
### <a name="remarks"></a>备注  
 重写此函数可实现自定义内存释放。 如果你重写此函数，你可能需要重写[Alloc](#alloc)和[Realloc](#realloc)以及。  
  
##  <a name="growfile"></a>  CMemFile::GrowFile  
 调用此函数可由几个`CMemFile`成员函数。  
  
```  
virtual void GrowFile(SIZE_T dwNewLen);
```  
  
### <a name="parameters"></a>参数  
 `dwNewLen`  
 内存文件的新大小。  
  
### <a name="remarks"></a>备注  
 如果你想要更改您可以覆盖它如何`CMemFile`会增大其文件。 默认实现调用[Realloc](#realloc)增长的现有块 (或[Alloc](#alloc)若要创建的内存块)，分配的倍数中的内存`nGrowBytes`构造函数中指定的值或[附加](#attach)调用。  
  
##  <a name="memcpy"></a>  CMemFile::Memcpy  
 调用此函数`CMemFile`重写[CFile::Read](../../mfc/reference/cfile-class.md#read)和[CFile::Write](../../mfc/reference/cfile-class.md#write)传输数据传入和传出的内存文件。  
  
```  
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,  
    const BYTE* lpMemSource,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>参数  
 `lpMemTarget`  
 将向其中复制源内存的内存块的指针。  
  
 `lpMemSource`  
 源内存块指针。  
  
 `nBytes`  
 要复制的字节数。  
  
### <a name="return-value"></a>返回值  
 `lpMemTarget` 的副本。  
  
### <a name="remarks"></a>备注  
 如果你想要更改的方式重写此函数的`CMemFile`未这些内存副本。  
  
##  <a name="realloc"></a>  CMemFile::Realloc  
 调用此函数`CMemFile`成员函数。  
  
```  
virtual BYTE* Realloc(
    BYTE* lpMem,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>参数  
 `lpMem`  
 指向要重新分配的内存块的指针。  
  
 `nBytes`  
 内存块的新大小。  
  
### <a name="return-value"></a>返回值  
 指向已重新分配 （和可能移动） 的内存块的指针或**NULL**如果重新分配失败。  
  
### <a name="remarks"></a>备注  
 重写此函数可实现自定义的内存重新分配。 如果你重写此函数，你可能需要重写[Alloc](#alloc)和[免费](#free)以及。  
  
## <a name="see-also"></a>请参阅  
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



