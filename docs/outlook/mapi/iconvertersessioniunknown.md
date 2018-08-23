---
title: "IConverterSession  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IConverterSession
api_type:
- COM
ms.assetid: 24f7a14a-aa6f-4045-054b-4a7aefef25e4
description: "Last modified: March 09, 2015"
---

# IConverterSession : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Allows conversions between MIME objects and MAPI messages. This can be useful in transporting messages across the Internet.
  
|||
|:-----|:-----|
|Provided by:  <br/> |CLSID_IConverterSession  <br/> |
|Interface identifier:  <br/> |IID_IConverterSession  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|**[SetAdrBook](iconvertersession-setadrbook.md)** <br/> |Specifies an optional MAPI Address Book that the MAPI to MIME converter uses to resolve ambiguous addresses when converting a MAPI message to a MIME stream.  <br/> |
|**[SetEncoding](iconvertersession-setencoding.md)** <br/> |Initializes the encoding to use during conversion.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
|**[MIMEToMAPI](iconvertersession-mimetomapi.md)** <br/> |Converts a MIME stream to a MAPI message.  <br/> |
|**[MAPIToMIMEStm](iconvertersession-mapitomimestm.md)** <br/> |Converts a MAPI message to a MIME stream.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
|**[SetTextWrapping](iconvertersession-settextwrapping.md)** <br/> |Sets the text wrapping width for a MIME stream that the converter returns in **MAPIToMIMEStm**.  <br/> |
|**[SetSaveFormat](iconvertersession-setsaveformat.md)** <br/> |Sets the format that the converter returns a MIME stream in **MAPIToMIMEStm**.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
|**[SetCharSet](iconvertersession-setcharset.md)** <br/> |Specifies an optional character set that the MAPI to MIME converter uses when converting a MAPI message to a MIME stream.  <br/> |
   
## Remarks

Call **SetEncoding** before using **MAPIToMIMEStm** to perform conversion. 
  
## See also



[About the MAPI-MIME Conversion API](about-the-mapi-mime-conversion-api.md)
  
[MAPI Constants](mapi-constants.md)

