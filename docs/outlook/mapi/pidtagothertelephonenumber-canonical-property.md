---
title: "PidTagOtherTelephoneNumber Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOtherTelephoneNumber
api_type:
- COM
ms.assetid: 60b11733-20c2-4fe9-8406-c3103b2852ba
description: "Last modified: March 09, 2015"
---

# PidTagOtherTelephoneNumber Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains an alternate telephone number for the recipient.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_OTHER_TELEPHONE_NUMBER, PR_OTHER_TELEPHONE_NUMBER_A, PR_OTHER_TELEPHONE_NUMBER_W  <br/> |
|Identifier:  <br/> |0x3A1F  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

These properties provide identification and access information for a recipient. They are defined by the recipient and their organization. 
  
These properties are used for a telephone number other than at the recipient's place of business, home, or office.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for address book templates.
    
[[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
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

