---
title: "PidTagContactAddressBookMultipleAddressFlag Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContactAddressBookMultipleAddressFlag
api_type:
- HeaderDef
ms.assetid: aefc34c5-1beb-44cf-a455-90f466e157ce
description: "Last modified: March 09, 2015"
---

# PidTagContactAddressBookMultipleAddressFlag Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a flag that is TRUE when the provider supports multiple email addresses per contact item.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAB_MULTI_ADDR_FLAG  <br/> |
|Identifier:  <br/> |0x6614  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Contact address book  <br/> |
   
## Remarks

If this property is TRUE, the provider does not allow contacts without email addresses. If FALSE, the provider shows all contacts whether or not they have a primary email address. Only the primary email address will be honored. This is a property on a Contact Address Book container, and a column in the table of Contact Address Book containers.
  
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

