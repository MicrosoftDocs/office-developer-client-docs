---
title: "PidTagMemberName Canonical Property"
description: Outlines the PidTagMemberName canonical property, which contains the display name of a member of the access control list (ACL) table.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMemberName
api_type:
- HeaderDef
ms.assetid: e19129bf-d07c-4d2e-9d4d-edbfda088ea7
---

# PidTagMemberName Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the display name of a member of the access control list (ACL) table.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_MEMBER_NAME, PR_MEMBER_NAME_A, PR_MEMBER_NAME_W  <br/> |
|Identifier:  <br/> |0x6672  <br/> |
|Data type:  <br/> |PT_STRING8  <br/> |
|Area:  <br/> |Access Control  <br/> |
   
## Remarks

These properties are used by the [IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md) interface to display the name of a member of an ACL table, which is a person or role with explicit rights on a folder or mailbox. 
  
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
  
> Contains definitions of properties listed as associated properties.
    
## See also



[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

