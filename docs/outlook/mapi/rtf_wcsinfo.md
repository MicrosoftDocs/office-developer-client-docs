---
title: "RTF_WCSINFO"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 0c94501e-0ec7-e836-33a7-adcf5a61b375
description: "This structure enables you to specify information to decompress the body of a message in compressed RTF and, return the body stream in its native format."
---

# RTF_WCSINFO

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This structure enables you to specify information to decompress the body of a message in compressed Rich Text Format (RTF) and, optionally, return the body stream in its native format.
  
## Quick info

```cpp
typedef struct { 
    ULONG size; 
    ULONG ulFlags; 
    ULONG ulInCodePage; 
    ULONG ulOutCodePage; 
} RTF_WCSINFO;

```

## Members

 _size_
  
> The size of the **RTF_WCSINFO** structure in number of bytes. 
    
 _ulFlags_
  
> This is the bitmask of option flags for the [WrapCompressedRTFStreamEx](wrapcompressedrtfstreamex.md) function. The supported option flags are: 
    
|Flag |Description |
|:-----|:-----|
|MAPI_MODIFY  <br/> |This indicates whether the client intends to write the wrapped stream interface that is returned. |
|STORE_UNCOMPRESSED_RTF  <br/> |This indicates whether the decompressed RTF is supposed to be written to the stream that is pointed to by the  _lpCompressedRTFStream_ pointer of the [WrapCompressedRTFStreamEx](wrapcompressedrtfstreamex.md) function. |
|MAPI_NATIVE_BODY  <br/> |This indicates whether the decompressed stream is also converted to the native body before returning the stream. This flag cannot be combined with the **MAPI_MODIFY** flag. |
   
 _ulInCodePage_
  
> This is the code page value of the message. Typically, this value is obtained from the [PidTagInternetCodepage Canonical Property](pidtaginternetcodepage-canonical-property.md) on the message. This value is only used when the **MAPI_NATIVE_BODY** flag is passed in  _ulFlags_. Otherwise, this value is ignored.
    
 _ulOutCodePage_
  
> This is the code page value of the returned decompressed stream that you want. If this is set to a non-zero value, the [WrapCompressedRTFStreamEx](wrapcompressedrtfstreamex.md) function converts the stream to the specified code page. If this is set to a zero value, MAPI decides which code page to use. This value is used only when the **MAPI_NATIVE_BODY** flag is passed in  _ulFlags_, and the body format is not RTF. Otherwise, this value is ignored.
    
## See also



[WrapCompressedRTFStreamEx](wrapcompressedrtfstreamex.md)

