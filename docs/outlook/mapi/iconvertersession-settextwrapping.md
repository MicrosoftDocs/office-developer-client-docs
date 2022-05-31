---
title: "IConverterSessionSetTextWrapping"
description: "IConverterSessionSetTextWrapping sets the text wrapping width for a MIME stream that the converter will return in IConverterSessionMAPIToMIMEStm." 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IConverterSession.SetTextWrapping
api_type:
- COM
ms.assetid: 8674b288-43a3-6376-35ca-9dbaa3a1851e
---

# IConverterSession::SetTextWrapping

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the text wrapping width for a MIME stream that the converter will return in [IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md).
  
```cpp
HRESULT IConverterSession::SetTextWrapping ( 
    BOOL    fWrapText, 
    ULONG   ulWrapWidth 
);
```

## Parameters

 *fWrapText* 
  
> [in] Whether to wrap text or not.
    
 *ulWrapWidth* 
  
> [in] The text wrapping width to use.
    
## Return value

S_OK
  
> The call was successful.
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MapiMime.cpp  <br/> |ImportEMLToIMessage  <br/> |MFCMAPI uses MimeToMAPI to convert an EML file to a MAPI message. |
|MapiMime.cpp  <br/> |ExportIMessageToEML  <br/> |MFCMAPI uses MAPIToMIMEStm to convert a MAPI message to an EML file. |
   
## See also



[IConverterSession : IUnknown](iconvertersessioniunknown.md)
  
[IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md)
  
[IConverterSession::MIMEToMAPI](iconvertersession-mimetomapi.md)
  
[IConverterSession::SetAdrBook](iconvertersession-setadrbook.md)
  
[IConverterSession::SetCharSet](iconvertersession-setcharset.md)
  
[IConverterSession::SetEncoding](iconvertersession-setencoding.md)
  
[IConverterSession::SetSaveFormat](iconvertersession-setsaveformat.md)


[MAPI Constants](mapi-constants.md)

