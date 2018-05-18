---
title: "PidTagSendInternetEncoding Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagSendInternetEncoding
api_type:
- COM
ms.assetid: ae408b4f-dee3-484b-a19c-f472cfa95996
description: "Last modified: March 09, 2015"
---

# PidTagSendInternetEncoding Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a bitmask of encoding preferences. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SEND_INTERNET_ENCODING  <br/> |
|Identifier:  <br/> |0x3A71  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

Set this property to indicate the encoding options used. 
  
This property contains the following flags:
  
BODY_ENCODING_HTML 
  
> Encode the message text in HTML. This flag is ignored unless the ENCODING_MIME flag is set. 
    
BODY_ENCODING_TEXT_AND_HTML 
  
> Encode the message text using text and HTML as Multipurpose Internet Mail Extensions (MIME) multipart alternatives. This flag is ignored unless the ENCODING_MIME flag is set. 
    
ENCODING_MIME 
  
> Encode the message using MIME. If this flag is not set, MAPI encodes the message text in plain text and the attachments in UUENCODE. 
    
ENCODING_PREFERENCE 
  
> Use the other flags in this bitmask to determine the encoding. If this flag is not set, MAPI leaves it to the messaging system to make encoding decisions. 
    
MAC_ATTACH_ENCODING_APPLEDOUBLE 
  
> Encode Macintosh attachments in Apple double mode. This flag is ignored unless the ENCODING_MIME flag is set. 
    
MAC_ATTACH_ENCODING_APPLESINGLE 
  
> Encode Macintosh attachments in Apple single mode. This flag is ignored unless the ENCODING_MIME flag is set. 
    
MAC_ATTACH_ENCODING_UUENCODE 
  
> Encode Macintosh attachments in UUENCODE. If the ENCODING_MIME flag is set, this flag is ignored and BinHex encoding is used instead. 
    
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard e-mail conventions to message objects.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for e-mail message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

