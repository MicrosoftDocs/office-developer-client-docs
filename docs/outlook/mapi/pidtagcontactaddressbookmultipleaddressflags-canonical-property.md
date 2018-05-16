---
title: "PidTagContactAddressBookMultipleAddressFlags Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContactAddressBookMultipleAddressFlags
api_type:
- HeaderDef
ms.assetid: ed3bc585-13f6-46a5-9e71-9c8513ddfc0a
description: "Last modified: March 09, 2015"
---

# PidTagContactAddressBookMultipleAddressFlags Canonical Property

  
  
**Applies to**: Outlook 
  
Contains flags that indicating whether the providers will support multiple e-mail addresses per contact item.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAB_MULTI_ADDR_FLAGS  <br/> |
|Identifier:  <br/> |0x6625  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |Contact address book  <br/> |
   
## Remarks

If the flags in this property are TRUE, the provider does not include contacts without e-mail addresses. Only the primary e-mail address will be honored. This is a property on a Contact Address Book profile section.
  
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

