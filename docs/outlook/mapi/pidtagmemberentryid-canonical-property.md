---
title: "PidTagMemberEntryId Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMemberEntryId
api_type:
- HeaderDef
ms.assetid: b1e166fd-7e15-4371-8510-63001317fb90
description: "Last modified: March 09, 2015"
---

# PidTagMemberEntryId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the directory object entry identifier of a system access control list (SACL) table member.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_MEMBER_ENTRYID  <br/> |
|Identifier:  <br/> |0x0FFF  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server Side Rules  <br/> |
   
## Remarks

This property is used by the [IExchangeModifyTable](iexchangemodifytableiunknown.md) interface to uniquely identify a person or role to whom the SACL applies. After a member is created in the SACL table, the **ENTRYID** cannot be changed. To change it, you must delete the table member and re-create it with a different **ENTRYID**.
  
## Related resources

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

