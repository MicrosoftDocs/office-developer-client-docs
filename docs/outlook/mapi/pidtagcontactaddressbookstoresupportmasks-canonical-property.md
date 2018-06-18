---
title: "PidTagContactAddressBookStoreSupportMasks Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContactAddressBookStoreSupportMasks
api_type:
- HeaderDef
ms.assetid: 68f5aac1-714c-48fc-a0cf-a0c0401a6070
description: "Last modified: March 09, 2015"
---

# PidTagContactAddressBookStoreSupportMasks Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains flags indicating the store's supported features.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAB_STORE_SUPPORT_MASKS  <br/> |
|Identifier:  <br/> |0x6621  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |Contact address book  <br/> |
   
## Remarks

This property is obtained from the stores which contains the Contacts folders. The Contact Address Book provider uses it to evaluate the adequacy of the store's supported features. It is a property on a Contact Address Book profile section. 
  
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

