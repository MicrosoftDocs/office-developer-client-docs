---
title: "WrapCompressedRTFStream"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.WrapCompressedRTFStream
api_type:
- COM
ms.assetid: 0949e066-aa28-4ede-ac88-b2dccd5098e8
description: "Last modified: March 09, 2015"
---

# WrapCompressedRTFStream

  
  
**Applies to**: Outlook 
  
Creates a text stream in uncompressed Rich Text Format (RTF) from the compressed format used in the **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```
HRESULT WrapCompressedRTFStream(
  LPSTREAM lpCompressedRTFStream,
  ULONG ulflags,
  LPSTREAM FAR * lpUncompressedRTFStream
);
```

## Parameters

 _lpCompressedRTFStream_
  
> [in] Pointer to a stream opened on the PR_RTF_COMPRESSED property of a message. 
    
 _ulFlags_
  
> [in] Bitmask of option flags for the function. The following flags can be set:
    
MAPI_MODIFY 
  
> Whether the client intends to read or write the wrapped stream interface that is returned. 
    
STORE_UNCOMPRESSED_RTF 
  
> Uncompressed RTF should be written to the stream pointed to by  _lpCompressedRTFStream_
    
 _lpUncompressedRTFStream_
  
> [out] Pointer to the location where **WrapCompressedRTFStream** returns a stream for the uncompressed RTF. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

If the MAPI_MODIFY flag is passed in the  _ulFlags_ parameter, the  _lpCompressedRTFStream_ parameter must already be open for reading and writing. New, uncompressed RTF text should be written into the stream interface returned in  _lpUncompressedRTFStream_. Because it is not possible to append the existing stream, the entire message text must be written. 
  
If zero is passed in the  _ulFlags_ parameter, then  _lpCompressedRTFStream_ may be opened read-only. Only the entire message text can be read out of the stream interface returned in  _lpUncompressedRTFStream_. It is not possible to search starting the middle of the stream. 
  
 **WrapCompressedRTFStream** assumes that the compressed stream's pointer is set to the beginning of the stream. Certain OLE **IStream** methods are not supported by the returned uncompressed stream. These include **IStream::Clone**, **IStream::LockRegion**, **IStream::Revert**, **IStream::Seek**, **IStream::SetSize**, **IStream::Stat**, and **IStream::UnlockRegion**. In order to copy to the entire stream, a read/write loop is needed. 
  
Because the client writes new RTF in uncompressed format, it should use **WrapCompressedRTFStream**, instead of directly writing to the stream. RTF-aware clients should search for the STORE_UNCOMPRESSED_RTF flag in the **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property and pass it to **WrapCompressed RTFStream** if it is set. 
  
## See also

#### Reference

[RTFSync](rtfsync.md)

