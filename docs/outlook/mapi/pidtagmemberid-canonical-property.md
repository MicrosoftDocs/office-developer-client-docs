---
title: "PidTagMemberId Canonical Property"
description: Outlines the PidTagMemberId canonical property, which contains the identifier of a table member that has described rights.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMemberId
api_type:
- HeaderDef
ms.assetid: 64faef3c-27b2-49d2-9d0c-8b9d33f1cb71
---

# PidTagMemberId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the identifier of a table member that has the described rights on a Microsoft Exchange Server folder or mailbox.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_MEMBER_ID  <br/> |
|Identifier:  <br/> |0x6671  <br/> |
|Data type:  <br/> |PT_I8  <br/> |
|Area:  <br/> |Access Control  <br/> |
   
## Remarks

This property returns an identifier unique to the table. A directory user identifier is associated with each member identifier and is given by this property. This property is used by the [IExchangeModifyTable](iexchangemodifytableiunknown.md) interface to retrieve the directory entry identifier of a member with explicit rights on a folder. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCPERM]](https://msdn.microsoft.com/library/944ddb65-6249-4c34-a46e-363fcd37195e%28Office.15%29.aspx)
  
> Handles the retrieval of folder permission lists that are stored on the server.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagMemberEntryId Canonical Property](pidtagmemberentryid-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

