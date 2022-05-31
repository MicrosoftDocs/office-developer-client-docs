---
title: "IConverterSessionSetSaveFormat"
description: "IConverterSessionSetSaveFormat sets the format in which the converter will return a MIME stream in IConverterSession::MAPIToMIMEStm."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IConverterSession.SetCharSet
api_type:
- COM
ms.assetid: e5308a94-5191-2109-a881-b4f4a7ff1c61
---

# IConverterSession::SetSaveFormat

**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the format in which the converter will return a MIME stream in [IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md).
  
```cpp
HRESULT IConverterSession::SetSaveFormat ( 
     MIMESAVETYPE mstSaveFormat 
);
```

## Parameters

_mstSaveFormat_
  
> [in] The save format to be used for a MIME stream. For more information, see the enum type [MIMESAVETYPE](https://msdn.microsoft.com/library/ms715128%28VS.85%29.aspx).
    
  - **SAVE_RFC1521**: Use MIME, which is the default.      
  - **SAVE_RFC822**: Use uuencode.
    
## Return values

S_OK
  
> The call was successful.
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MapiMime.cpp  <br/> |ImportEMLToIMessage  <br/> |MFCMAPI uses MimeToMAPI to convert an EML file to a MAPI message. |
|MapiMime.cpp  <br/> |ExportIMessageToEML  <br/> |MFCMAPI uses MAPIToMIMEStm to convert a MAPI message to an EML file. |
   
## See also

- [IConverterSession : IUnknown](iconvertersessioniunknown.md)
- [IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md)
- [IConverterSession::MIMEToMAPI](iconvertersession-mimetomapi.md)
- [IConverterSession::SetAdrBook](iconvertersession-setadrbook.md)
- [IConverterSession::SetCharSet](iconvertersession-setcharset.md)
- [IConverterSession::SetEncoding](iconvertersession-setencoding.md)
- [IConverterSession::SetTextWrapping](iconvertersession-settextwrapping.md)
- [MAPI Constants](mapi-constants.md)

