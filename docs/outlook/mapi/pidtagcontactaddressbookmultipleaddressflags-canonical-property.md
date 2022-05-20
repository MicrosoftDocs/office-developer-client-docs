---
title: "PidTagContactAddressBookMultipleAddressFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagContactAddressBookMultipleAddressFlags
api_type:
- HeaderDef
ms.assetid: ed3bc585-13f6-46a5-9e71-9c8513ddfc0a
description: "Last modified: March 09, 2015"
---

# PidTagContactAddressBookMultipleAddressFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains flags that indicating whether the providers will support multiple email addresses per contact item.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAB_MULTI_ADDR_FLAGS  <br/> |
|Identifier:  <br/> |0x6625  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |Contact address book  <br/> |
   
## Remarks

If the flags in this property are TRUE, the provider does not include contacts without email addresses. Only the primary email address will be honored. This is a property on a Contact Address Book profile section.
  
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

