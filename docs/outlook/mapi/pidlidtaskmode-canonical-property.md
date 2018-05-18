---
title: "PidLidTaskMode Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidTaskMode
api_type:
- COM
ms.assetid: 185db683-301a-4d91-a583-6959853fa1ad
description: "Last modified: March 09, 2015"
---

# PidLidTaskMode Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the assignment status of the task.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskMode  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008518  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

The value must be one of the following.
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |The task is not assigned.  <br/> |
|0x00000001  <br/> |The task is embedded in a task request.  <br/> |
|0x00000002  <br/> |The task was accepted by the task assignee.  <br/> |
|0x00000003  <br/> |The task was rejected by the task assignee.  <br/> |
|0x00000004  <br/> |The task is embedded in a task update.  <br/> |
|0x00000005  <br/> |The task was assigned to the task assigner.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOTASK]](http://msdn.microsoft.com/library/55600ec0-6195-4730-8436-59c7931ef27e%28Office.15%29.aspx)
  
> Defines several objects that model the electronic equivalent of tasks, task assignments, and task updates.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

