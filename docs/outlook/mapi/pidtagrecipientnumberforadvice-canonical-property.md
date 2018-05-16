---
title: "PidTagRecipientNumberForAdvice Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRecipientNumberForAdvice
api_type:
- COM
ms.assetid: 636c1e75-3024-43ca-a7dd-1bb480dfbb5b
description: "Last modified: March 09, 2015"
---

# PidTagRecipientNumberForAdvice Canonical Property

  
  
**Applies to**: Outlook 
  
This property contains a message recipient's telephone number to call to advise of the physical delivery of a message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RECIPIENT_NUMBER_FOR_ADVICE, PR_RECIPIENT_NUMBER_FOR_ADVICE_A, PR_RECIPIENT_NUMBER_FOR_ADVICE_W  <br/> |
|Identifier:  <br/> |0x0C14  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI Recipient  <br/> |
   
## Remarks

These properties are meant to be used in conjunction with delivery to a physical destination, rather than an electronic mailbox, when the human recipient is not expected to be present at delivery. An example is the telephone number on a fax cover sheet.
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

