---
title: "IConverterSessionMAPIToMIMEStm"
 
 
ms.date: 9/20/2017
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IConverterSession.MAPIToMIMEStm
api_type:
- COM
ms.assetid: 8660c701-f7f4-8d92-7984-5dae7f677783
description: "Last modified: September 20, 2017"
---

# IConverterSession::MAPIToMIMEStm
 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Converts a MAPI message to a MIME stream.
  
```cpp
HRESULT IConverterSession::MAPIToMIMEStm( 
    LPMESSAGE pmsg, 
    LPSTREAM pstm, 
    ULONG ulFlags 
);
```

## Parameters

 _pmsg_
  
> [in] Pointer to the message to convert. See mapidefs.h for the type definition of **LPMESSAGE**.
    
 _pstm_
  
> [out] [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) interface to output the stream. 
    
 _ulFlags_
  
>  [in] Flags that indicate specific actions for the converter: 
    
CCSF_8BITHEADERS
  
> The converter should allow 8-bit headers.
    
CCSF_EMBEDDED_MESSAGE
  
> Sent/unsent information is persisted in X-Unsent.
    
CCSF_GLOBAL_MESSAGE
  
> The converter should build an international message (EAI/RFC6530).
    
CCSF_INCLUDE_BCC
  
> BCC recipients of the MAPI message should be included in the MIME stream.
    
CCSF_NO_MSGID
  
> Do not include Message-Id field in outgoing messages.
    
CCSF_NOHEADERS
  
> The converter should ignore the headers of the outside message.
    
CCSF_PLAIN_TEXT_ONLY
  
> The converter should just send plain text.
    
CCSF_SMTP
  
> The converter is being passed an SMTP message. This flag must always be set.
    
CCSF_USE_RTF
  
> The converter should convert from HTML to RTF format in the MIME message.
    
CCSF_USE_TNEF
  
> The converter should use Transport Neutral Encapsulation Format (TNEF) format in the MIME message.
    
## Return values

E_INVALIDARG
  
> Invalid flags were passed, or  *pmsg*  or  *pstm*  is NULL. 
    
## Remarks

Supported only for standard Outlook message types.
  
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
  
[IConverterSession::SetTextWrapping](iconvertersession-settextwrapping.md)
  
[PidTagMessageEditorFormat Canonical Property](pidtagmessageeditorformat-canonical-property.md)
  
[PidLidUseTnef Canonical Property](pidlidusetnef-canonical-property.md)


[MAPI Constants](mapi-constants.md)

