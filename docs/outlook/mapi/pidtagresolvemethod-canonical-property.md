---
title: "PidTagResolveMethod Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagResolveMethod
api_type:
- COM
ms.assetid: 30d23c19-e0da-4511-9361-761153259216
description: "Last modified: March 09, 2015"
---

# PidTagResolveMethod Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a folder's conflict resolution value.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RESOLVE_METHOD  <br/> |
|Identifier:  <br/> |0x3FE7  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

This property on the folder containing the conflict resolution message will indicate how to resolve the conflict. This property is not required. However, if it is set, flags other than the following must not be present:
  
|||
|:-----|:-----|
|RESOLVE_METHOD_DEFAULT (0x00000000)  <br/> |Conflict resolve message should be generated.  <br/> |
|RESOLVE_METHOD_LAST_WRITER_WINS (0x00000001)  <br/> |Overwrite target message with current changes being applied.  <br/> |
|RESOLVE_NO_CONFLICT_NOTIFICATION (0x00000002)  <br/> |Do not send conflict notification message when generating conflict resolve message in public folder.  <br/> |
   
A client or server must not generate a conflict resolve message for associated messages. These messages must be resolved by using **RESOLVE_METHOD_LAST_WRITER_WINS** semantics. 
  
## Related resources

### Protocol Specifications

[[MS-OXCSYNC]](http://msdn.microsoft.com/library/fd3e23ef-341a-4a8c-a0e9-6afecbb11c40%28Office.15%29.aspx)
  
> Handles synchronizing messaging object data between a server and a client.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Defines the basic data structures that are used in remote operations.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

