---
title: "PidTagContactAddressBookStoreSupportMask Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContactAddressBookStoreSupportMask
api_type:
- HeaderDef
ms.assetid: 34f649c8-29bf-470f-9b05-31b69d069259
description: "Last modified: March 09, 2015"
---

# PidTagContactAddressBookStoreSupportMask Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the **PR_STORE_SUPPORT_MASK** ( [PidTagStoreSupportMask](pidtagcontactaddressbookstoresupportmask-canonical-property.md)) property obtained from the store that contains the Contacts folder.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAB_STORE_SUPPORT_MASK  <br/> |
|Identifier:  <br/> |0x6611  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Contact address book  <br/> |
   
## Remarks

The Contact Address Book provider uses this property to evaluate the adequacy of the store's supported features. This is a property on a Contact Address Book container, and a column in the table of Contact Address Book containers.
  
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

