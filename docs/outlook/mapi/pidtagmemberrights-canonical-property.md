---
title: "PidTagMemberRights Canonical Property"
description: Outlines the PidTagMemberRights canonical property, which contains a set of bits that indicated the rights of this member on a folder or mailbox.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMemberRights
api_type:
- HeaderDef
ms.assetid: 3e526b93-1f64-41ea-b43c-5b03fe1c56ed
---

# PidTagMemberRights Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a set of bits that indicated the rights of this member on a folder or mailbox.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_MEMBER_RIGHTS  <br/> |
|Identifier:  <br/> |0x6673  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Access Control  <br/> |
   
## Remarks

This property is used by the [IExchangeModifyTable](iexchangemodifytableiunknown.md) interface to define rights of a member on a folder. These rights can be displayed and modified. The following values are rights defined for this property. 
  
frightsReadAny
  
> Member can read any messages.
    
frightsCreate
  
> Member can create messages.
    
frightsEditOwned
  
> Member can edit any messages owned by the user.
    
frightsDeleteOwned
  
> Member can delete any messages owned by the user.
    
frightsEditAny
  
> Member can edit any message.
    
frightsDeleteAny
  
> Member can delete any message.
    
frightsCreateSubfolder
  
> Member can create subfolders for the folder.
    
frightsOwner
  
> Member has all the previous rights on the folder.
    
frightsContact
  
> Member can have your name appear as the contact on the folder.
    
frightsVisible
  
> Member can see that the folder exists.
    
rightsNone
  
> Member does not have rights on the folder.
    
rightsReadOnly
  
> Member can read any message in the folder.
    
rightsReadWrite
  
> Member can read from and write to any message in the folder.
    
rightsAll
  
> Member has all the previous rights on the folder.
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFOLD]](https://msdn.microsoft.com/library/c0f31b95-c07f-486c-98d9-535ed9705fbf%28Office.15%29.aspx)
  
> Handles folder operations.
    
[[MS-OXCPERM]](https://msdn.microsoft.com/library/944ddb65-6249-4c34-a46e-363fcd37195e%28Office.15%29.aspx)
  
> Handles the retrieval of folder permission lists that are stored on the server.
    
[[MS-OXODLGT]](https://msdn.microsoft.com/library/01a89b11-9c43-4c40-b147-8f6a1ef5a44f%28Office.15%29.aspx)
  
> Specifies methods for connecting to and configuring mailboxes as delegates, and interactions with message and calendar items when they act on behalf of another user.
    
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

