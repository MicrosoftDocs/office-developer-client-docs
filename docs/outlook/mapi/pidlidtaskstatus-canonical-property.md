---
title: "PidLidTaskStatus Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidTaskStatus
api_type:
- COM
ms.assetid: 809776b7-ff00-4a52-84b9-8b5fb5f5c3e3
description: "Last modified: March 09, 2015"
---

# PidLidTaskStatus Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the status of the user's progress on the task.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskStatus  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x00008101  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

The value of this property must be set to one of the following.
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |The user has not started work on the task. If this value is set, **dispidPercentComplete** ([PidLidPercentComplete](pidlidpercentcomplete-canonical-property.md)) must be 0.0.  <br/> |
|0x00000001  <br/> |The user's work on this task is in progress. If this value is set, **dispidPercentComplete** must be greater than 0.0 and less than 1.0.  <br/> |
|0x00000002  <br/> |The user's work on this task is complete. If this value is set, **dispidPercentComplete** must be 1.0, **dispidTaskDateCompleted** ([PidLidTaskDateCompleted](pidlidtaskdatecompleted-canonical-property.md)) must be the current date, and **dispidTaskComplete** ([PidLidTaskComplete](pidlidtaskcomplete-canonical-property.md)) must be TRUE.  <br/> |
|0x00000003  <br/> |The user is waiting on somebody else.  <br/> |
|0x00000004  <br/> |The user has deferred work on the task.  <br/> |
   
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOTASK]](http://msdn.microsoft.com/library/55600ec0-6195-4730-8436-59c7931ef27e%28Office.15%29.aspx)
  
> Defines several objects that model the electronic equivalent of tasks, task assignments, and task updates.
    
[[MS-OXOFLAG]](http://msdn.microsoft.com/library/f1e50be4-ed30-4c2a-b5cb-8ff3aaaf9b91%28Office.15%29.aspx)
  
> Specifies the properties and operations related to flagging.
    
[[MS-OXOSFLD]](http://msdn.microsoft.com/library/a60e9c16-2ba8-424b-b60c-385a8a2837cb%28Office.15%29.aspx)
  
> Specifies the properties and operations for creating and locating the special folders in a mailbox.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard e-mail conventions to message objects.
    
[[MS-OXCICAL]](http://msdn.microsoft.com/library/a685a040-5b69-4c84-b084-795113fb4012%28Office.15%29.aspx)
  
> Converts between IETF RFC2445, RFC2446, and RFC2447, and appointment and meeting objects.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles the order and flow for data transfers between a client and server.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[PidLidPercentComplete Canonical Property](pidlidpercentcomplete-canonical-property.md)
  
[PidLidTaskDateCompleted Canonical Property](pidlidtaskdatecompleted-canonical-property.md)
  
[PidLidTaskComplete Canonical Property](pidlidtaskcomplete-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

