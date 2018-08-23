---
title: "PidTagInConflict Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagInConflict
api_type:
- HeaderDef
ms.assetid: e83c05c6-a7c0-486c-a112-58a39255767a
description: "Last modified: March 09, 2015"
---

# PidTagInConflict Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains TRUE when the attachment represents an alternate replica.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_IN_CONFLICT  <br/> |
|Identifier:  <br/> |0x666C  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Conflict note  <br/> |
   
## Remarks

The email client and server must generate a conflict resolve message when detecting a conflict against the current version of a message in the replica during synchronization. It is important to understand that it is possible that the current version of the message in the local replica was transmitted during the current synchronization operation. This will happen when the conflict already exists on the server before any of the conflicting messages were downloaded to the local replica. A conflict resolve message must be synchronized as independent replicas with conflicting PCLs. The conflict resolve message itself must not be synchronized between client and server; only the independent replicas should be exchanged. The synchronization partner must then generate a new message that matches the structure of the conflict message. Therefore, it is important that client and server use the same algorithm to detect the "winner" item. The following rules must be applied to detect the "winner":
  
1. Last modification time.
    
2. Higher CN GUID (using memory compare) to break tie.
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles synchronizing messaging object data between a server and a client.
    
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

