---
title: "PidTagContactAddressBookStoreSupportMask Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagContactAddressBookStoreSupportMask
api_type:
- HeaderDef
ms.assetid: 34f649c8-29bf-470f-9b05-31b69d069259
description: "Contains the PR_STORE_SUPPORT_MASK property obtained from the store that contains the Contacts folder."
---

# PidTagContactAddressBookStoreSupportMask Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagcontactaddressbookstoresupportmask-canonical-property.md)) property obtained from the store that contains the Contacts folder.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAB_STORE_SUPPORT_MASK  <br/> |
|Identifier:  <br/> |0x6611  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Contact address book  <br/> |
   
## Remarks

The Contact Address Book provider uses this property to evaluate the adequacy of the store's supported features. This is a property on a Contact Address Book container, and a column in the table of Contact Address Book containers.
  
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

