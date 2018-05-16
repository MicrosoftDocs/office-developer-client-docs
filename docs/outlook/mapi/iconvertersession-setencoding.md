---
title: "IConverterSessionSetEncoding"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IConverterSession.SetCharSet
api_type:
- COM
ms.assetid: a9624d3f-a636-0267-5cbd-de0db42f9c22
description: "Last modified: March 09, 2015"
---

# IConverterSession::SetEncoding

  
  
**Applies to**: Outlook 
  
Initializes the encoding to be used during conversion.
  
```
HRESULT IConverterSession:: SetEncoding ( 
     ENCODINGTYPE et 
);
```

## Parameters

 _et_
  
> An [ENCODINGTYPE](http://msdn.microsoft.com/en-us/library/aa374936%28VS.85%29.aspx) value. Only the following values are supported: 
    
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
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MapiMime.cpp  <br/> |ImportEMLToIMessage  <br/> |MFCMAPI uses MimeToMAPI to convert an EML file to a MAPI message.  <br/> |
|MapiMime.cpp  <br/> |ExportIMessageToEML  <br/> |MFCMAPI uses MAPIToMIMEStm to convert a MAPI message to an EML file.  <br/> |
   
## See also

#### Reference

[IConverterSession : IUnknown](iconvertersessioniunknown.md)
  
[IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md)
  
[IConverterSession::MIMEToMAPI](iconvertersession-mimetomapi.md)
  
[IConverterSession::SetAdrBook](iconvertersession-setadrbook.md)
  
[IConverterSession::SetCharSet](iconvertersession-setcharset.md)
  
[IConverterSession::SetSaveFormat](iconvertersession-setsaveformat.md)
  
[IConverterSession::SetTextWrapping](iconvertersession-settextwrapping.md)
#### Concepts

[MAPI Constants](mapi-constants.md)

