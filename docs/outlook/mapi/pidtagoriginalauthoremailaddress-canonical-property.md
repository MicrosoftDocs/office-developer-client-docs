---
title: "PidTagOriginalAuthorEmailAddress Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginalAuthorEmailAddress
api_type:
- COM
ms.assetid: 67cda756-ba71-4f29-a601-55359e44d93b
description: "Contains the email address of the author of the first version of a message, which is the message before being forwarded or replied to."
---

# PidTagOriginalAuthorEmailAddress Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the email address of the author of the first version of a message, that is, the message before being forwarded or replied to.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_AUTHOR_EMAIL_ADDRESS, PR_ORIGINAL_AUTHOR_EMAIL_ADDRESS_A, PR_ORIGINAL_AUTHOR_EMAIL_ADDRESS_W  <br/> |
|Identifier:  <br/> |0x007A  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

These properties are examples of the address properties for the author of a message. At first submission of the message, the client application should set these properties to the value of the **PR_SENDER_EMAIL_ADDRESS** ([PidTagSenderEmailAddress](pidtagsenderemailaddress-canonical-property.md)) property. It is never changed when the message is forwarded or replied to.
  
The original author properties allow for preservation of information from outside the local messaging domain. When a message arrives from another messaging domain, such as from the Internet, these properties provide a way to ensure that original information is not lost.
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

