---
title: "PidTagCallbackTelephoneNumber Canonical Property"
description: Outlines the PidTagCallbackTelephoneNumber canonical property, which contains a telephone number that the message recipient can use to reach the sender. 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagCallbackTelephoneNumber
api_type:
- HeaderDef
ms.assetid: e78d7e65-23a4-4359-b057-e06131cabf25
---

# PidTagCallbackTelephoneNumber Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a telephone number that the message recipient can use to reach the sender. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_CALLBACK_TELEPHONE_NUMBER, PR_CALLBACK_TELEPHONE_NUMBER_A, PR_CALLBACK_TELEPHONE_NUMBER_W  <br/> |
|Identifier:  <br/> |0x3A02  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

These properties are examples of the properties that provides identification and access information about a recipient. They are defined by the recipient and the recipient's organization. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contact and personal distribution list objects.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

