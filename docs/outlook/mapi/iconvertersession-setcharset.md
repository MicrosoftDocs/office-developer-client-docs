---
title: "IConverterSessionSetCharSet"
 
 
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
ms.assetid: 25af3683-3a65-2d39-6f6e-76c8d36f866d
description: "Last modified: March 09, 2015"
---

# IConverterSession::SetCharSet

  
  
**Applies to**: Outlook 
  
Specifies an optional character set that the MAPI to MIME converter use when converting a MAPI message to a MIME stream.
  
```
HRESULT SetCharset( 
     BOOL fApply, 
     HCHARSET hcharset, 
     CSETAPPLYTYPE csetapplytype); 
```

## Parameters

 _fApply_
  
> [in] Indicates whether to use a specific character set for the conversion. Set this parameter to **true** to apply the character set in subsequent conversions. Set this parameter to **false** if you no longer want to apply any specific character set and return to the defaults for subsequent messages. 
    
 _hcharset_
  
> [in] A handle to a character set as defined in mimeole.h of Windows Mail. Specify **null** to specify that you do not want to apply any specific character set. For non- **null** values, use a function such as [MimeOleGetCodePageCharset](http://msdn.microsoft.com/en-us/library/ms714746%28VS.85%29.aspx) to obtain a handle to the character set. 
    
 _csetapplytype_
  
> [in] Indicates how to apply a character set to convert a message, as defined in mimeole.h of Windows Mail.
    
## Return value

S_OK
  
> The function call is successful.
    
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
  
[IConverterSession::SetEncoding](iconvertersession-setencoding.md)
  
[IConverterSession::SetSaveFormat](iconvertersession-setsaveformat.md)
  
[IConverterSession::SetTextWrapping](iconvertersession-settextwrapping.md)

