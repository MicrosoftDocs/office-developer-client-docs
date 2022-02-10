---
title: "IConverterSessionSetEncoding"
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
ms.assetid: a9624d3f-a636-0267-5cbd-de0db42f9c22
description: "Last modified: March 09, 2015"
---

# IConverterSession::SetEncoding

**Applies to**: Outlook 2013 | Outlook 2016 
  
Initializes the encoding to be used during conversion.
  
```cpp
HRESULT IConverterSession:: SetEncoding ( 
     ENCODINGTYPE et 
);
```

## Parameters

_et_
  
> An [ENCODINGTYPE](https://msdn.microsoft.com/library/aa374936%28VS.85%29.aspx) value. Only the following values are supported: 
    
   - IET_BASE64
   - IET_UUENCODE
   - IET_QP
   - IET_7BIT
   - IET_8BIT
    
## Return value

E_INVALIDARG
  
> The encoding type passed was invalid.
    
## Remarks

Call **SetEncoding** before using [IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md) to perform conversion. 
  
Use **SetEncoding** to set the encoding for only the outermost message body of a mail item. Microsoft Outlook 2010 and Microsoft Outlook 2013 choose the encoding for any individual attachments. 
  
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
- [IConverterSession::SetSaveFormat](iconvertersession-setsaveformat.md)
- [IConverterSession::SetTextWrapping](iconvertersession-settextwrapping.md)
- [MAPI Constants](mapi-constants.md)

