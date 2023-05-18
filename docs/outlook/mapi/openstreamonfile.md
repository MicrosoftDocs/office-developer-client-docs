---
title: "OpenStreamOnFile"
description: "OpenStreamOnFile allocates and initializes an OLE IStream object to access the contents of a file. This function takes an ANSI string as the file name."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.OpenStreamOnFile
api_type:
- COM
ms.assetid: 01fa459f-597d-4b16-b340-a79fb270cd71
---

# OpenStreamOnFile

**Applies to**: Outlook 2013 | Outlook 2016
  
Allocates and initializes an OLE **IStream** object to access the contents of a file. This function takes an ANSI string as the file name including the path and the file extension, therefore, use of the Unicode version of this function, [OpenStreamOnFileW](openstreamonfilew.md), is recommended.
  
|**Item**|**Value**|
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |

```cpp
HRESULT STDMETHODCALLTYPE OpenStreamOnFile(
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPFREEBUFFER lpFreeBuffer,
  ULONG ulFlags,
  LPSTR lpszFileName,
  LPSTR lpszPrefix,
  LPSTREAM FAR * lppStream
);
```

## Parameters

 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory.

 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory.

 _ulFlags_
  
> [in] Bitmask of flags used to control the creation or opening of the file to be accessed through the OLE **IStream** object. The following flags can be set:

SOF_UNIQUEFILENAME
  
> A temporary file is to be created for the **IStream** object. If this flag is set, the STGM_CREATE and STGM_READWRITE flags should also be set.

STGM_CREATE
  
> The file is to be created even if one already exists. If the  _lpszFileName_ parameter is not set, both this flag and STGM_DELETEONRELEASE must be set. If STGM_CREATE is set, the STGM_READWRITE flag must also be set.

STGM_DELETEONRELEASE
  
> The file is to be deleted when the **IStream** object is released. If the  _lpszFileName_ parameter is not set, both this flag and STGM_CREATE must be set.

STGM_READ
  
> The file is to be created or opened with read-only access.

STGM_READWRITE
  
> The file is to be created or opened with read/write permission. If this flag is not set, the STGM_CREATE flag must not be set either.

 _lpszFileName_
  
> [in] The filename, including path and extension, of the file for which **OpenStreamOnFile** initializes the **IStream** object. If the SOF_UNIQUEFILENAME flag is set, _lpszFileName_ contains the path to the directory in which to create a temporary file. If  _lpszFileName_ is NULL, **OpenStreamOnFile** obtains an appropriate path from the system, and both the STGM_CREATE and STGM_DELETEONRELEASE flags must be set.

 _lpszPrefix_
  
> [in] The prefix for the filename on which **OpenStreamOnFile** initializes the **IStream** object. If set, the prefix must contain not more than three characters. If  _lpszPrefix_ is NULL, a prefix of "SOF" is used.

 _lppStream_
  
> [out] Pointer to a pointer to an object exposing the **IStream** interface.

## Return value

S_OK
  
> The call succeeded and has returned the expected value or values.

MAPI_E_NO_ACCESS
  
> The file could not be accessed due to insufficient user permissions or because read-only files cannot be modified.

MAPI_E_NOT_FOUND
  
> The designated file does not exist.

## Remarks

The **OpenStreamOnFile** function has two important uses, distinguished by the setting of the SOF_UNIQUEFILENAME flag. When this flag is not set, **OpenStreamOnFile** opens an **IStream** object on an existing file, for example to copy its contents to the **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) property of an attachment using the **IStream::CopyTo** method. In this case the _lpszFileName_ parameter specifies the path and filename of the file.
  
When SOF_UNIQUEFILENAME is set, **OpenStreamOnFile** creates a temporary file to hold data for an **IStream** object. For this usage, the _lpszFileName_ parameter can optionally designate the path to the directory where the file is to be created, and the  _lpszPrefix_ parameter can optionally specify a prefix for the filename.
  
When the calling client application or service provider is finished with the **IStream** object, it should free it by calling the OLE **IStream::Release** method.
  
MAPI uses the functions pointed to by _lpAllocateBuffer_ and _lpFreeBuffer_ for most memory allocation and deallocation, in particular to allocate memory for use by client applications when calling object interfaces such as [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPITable::QueryRows](imapitable-queryrows.md).
  
## Notes to callers

The SOF_UNIQUEFILENAME flag is used to create a temporary file with a name unique to the messaging system. If this flag is set, the _lpszFileName_ parameter specifes the path for the temporary file, and the _lpszPrefix_ parameter contains the prefix characters of the filename. The constructed filename is \<prefix>HHHH.TMP, where HHHH is a hexadecimal number. If  _lpszFileName_ is NULL, the file will be created in the temporary file directory that is returned from the Windows function **GetTempPath**, or the current directory if no temporary file directory has been designated.
  
If the SOF_UNIQUEFILENAME flag is not set, _lpszPrefix_ is ignored, and _lpszFileName_ should contain the fully qualified path and filename of the file to be opened or created. The file will be opened or created based on the other flags that are set in _ulFlags_.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|File.cpp  <br/> |WriteAttachStreamToFile  <br/> |MFCMAPI uses the **OpenStreamOnFile** method to open a stream on a file so an attachment can be written out to it. |

## See also

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
