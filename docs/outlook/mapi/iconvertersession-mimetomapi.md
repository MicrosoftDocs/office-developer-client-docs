---
title: "IConverterSessionMIMEToMAPI"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IConverterSession.MIMEToMAPI
api_type:
- COM
ms.assetid: ee190ba7-9e71-97e4-7bf1-7b97adc73eed
description: "Last modified: March 09, 2015"
---

# IConverterSession::MIMEToMAPI

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Converts a MIME stream to a MAPI message.
  
```cpp
HRESULT IConverterSession:: MIMEToMAPI ( 
     LPSTREAM pstm, 
     LPMESSAGE pmsg, 
     LPCSTR pszSrcSrv, 
     ULONG ulFlags 
);
```

## Parameters

 _pstm_
  
> [in] [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) interface to a MIME stream. 
    
 _pmsg_
  
> [out] Pointer to the message to load. See mapidefs.h for the type definition of **LPMESSAGE**.
    
 _pszSrcSrv_
  
> [in] This value must be **null**.
    
 _ulFlags_
  
> [in] This parameter identifies any special action to be taken during the conversion. It must be zero (0) if no specific action is to be taken, or a combination of the following values:
    
CCSF_EMBEDDED_MESSAGE
  
> Sent/unsent information is persisted in X-Unsent.
    
CCSF_SMTP
  
> The MIME stream is for a Simple MAPI Transfer Protocol (SMTP) message.
    
CCSF_INCLUDE_BCC
  
> BCC recipients of the MIME stream should be included in the MAPI message.
    
CCSF_USE_RTF
  
> The HTML body of the MIME stream should be converted to Rich Text Format (RTF) in the MAPI message.

CCSF_GLOBAL_MESSAGE
> The converter should handle the MIME stream as an international message (EAI/RFC6530). Not supported on Outlook 2013.
    
## Return value

E_INVALIDARG
  
> Indicates that  _pstm_ is **null**,  _pmsg_ is **null**, or  _ulFlags_ is invalid. 
    
## Remarks

If you have specified **CCSF_USE_RTF** as part of  _ulFlags_ and the destination message store supports both HTML and RTF, the MAPI message will be converted to either HTML or RTF. If the message is converted to RTF, the converted format will be compressed RTF, any HTML will be embedded in the compressed RTF string, and the string will be contained in the [PidTagRtfCompressed Canonical Property](pidtagrtfcompressed-canonical-property.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MapiMime.cpp  <br/> |ImportEMLToIMessage  <br/> |MFCMAPI uses MimeToMAPI to convert an EML file to a MAPI message.  <br/> |
|MapiMime.cpp  <br/> |ExportIMessageToEML  <br/> |MFCMAPI uses MAPIToMIMEStm to convert a MAPI message to an EML file.  <br/> |
   
## See also



[IConverterSession : IUnknown](iconvertersessioniunknown.md)
  
[IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md)
  
[IConverterSession::SetAdrBook](iconvertersession-setadrbook.md)
  
[IConverterSession::SetCharSet](iconvertersession-setcharset.md)
  
[IConverterSession::SetEncoding](iconvertersession-setencoding.md)
  
[IConverterSession::SetSaveFormat](iconvertersession-setsaveformat.md)
  
[IConverterSession::SetTextWrapping](iconvertersession-settextwrapping.md)


[MAPI Constants](mapi-constants.md)

