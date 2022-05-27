---
title: "PidTagContainerFlags Canonical Property"
description: Outlines the PidTagContainerFlags canonical property, which contains a bitmask of flags describing capabilities of an address book container.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagContainerFlags
api_type:
- HeaderDef
ms.assetid: 66b8d333-227e-464d-8cf9-cd8a5ff15efb
---

# PidTagContainerFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a bitmask of flags describing capabilities of an address book container. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAINER_FLAGS  <br/> |
|Identifier:  <br/> |0x3600  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

One or more of the following flags can be set for the bitmask:
  
AB_FIND_ON_OPEN 
  
> Displays a dialog box to request a restriction before displaying any contents of the container. 
    
AB_MODIFIABLE 
  
> Entries can be added to and removed from the container. This flag does not indicate whether any entries in the container can be modified.
    
AB_RECIPIENTS 
  
> The container can hold recipients. This flag does not indicate whether any recipients are actually present in the container, or whether they can be added or removed. 
    
AB_SUBCONTAINERS 
  
> The container can hold child containers. This flag does not indicate whether any subcontainers are actually present in the container, nor whether they can be added or removed. AB_SUBCONTAINERS must be set for the container to support [IMAPIContainer::GetHierarchyTable](imapicontainer-gethierarchytable.md). 
    
AB_UNMODIFIABLE 
  
> Entries cannot be added to or removed from the container. This flag does not indicate whether any entries in the container can be modified. 
    
The AB_FIND_ON_OPEN flag is highly recommended for containers used with online services or with slow connections to servers. When a container is opened that has AB_FIND_ON_OPEN set, a **Find** dialog box is presented to the user to restrict the displayed messaging users. Even a partial specification limiting the messaging users can dramatically speed up a display of the contents. 
  
Either the AB_MODIFIABLE or AB_UNMODIFIABLE flag must be set. Both flags can be set to indicate that the container does not know whether it can be modified or not, for example if modification depends on the user's access rights. In this case, a client application must attempt a call and examine the return code to determine the container's capabilities. A client typically starts by examining AB_MODIFIABLE. If it is set, the client makes a call that attempts to modify the container and checks the return value. 
  
The AB_MODIFIABLE flag does not indicate what types of entries can be added to the container. To determine this, the client should use the appropriate [OpenProperty](imapiprop-openproperty.md) method to open the container's **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property. Opening **PR_CREATE_TEMPLATES** causes the container's one-off table to be returned, listing the kinds of entries that can be created in the container. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
[[MS-NSPI]](https://msdn.microsoft.com/library/6dd0a3ea-b4d4-4a73-a857-add03a89a543%28Office.15%29.aspx)
  
> Handles a client's communications with a Name Service Provider Interface (NSPI) server.
    
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

