---
title: "PidTagAccessControlListTable Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAccess
api_type:
- HeaderDef
ms.assetid: 48667fda-ddc4-42ac-9231-761db0a4c1a9
description: "Last modified: March 09, 2015"
---

# PidTagAccessControlListTable Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a table that consists of all the system access control lists (SACL) applied to a folder.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ACL_TABLE  <br/> |
|Identifier:  <br/> |0x3FE0  <br/> |
|Data type:  <br/> |PT_OBJECT  <br/> |
|Area:  <br/> |Access Control  <br/> |
   
## Remarks

This property is present on all folder objects on an Exchange Server. Values included in this property are used for reading and modifying access control lists (ACLs) on folders. You can use the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method with the **IID_IExchangeModifyTable** interface identifier to obtain an [IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md) interface to the ACL table on a folder. You can use this interface to read and modify those ACLs. 
  
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

