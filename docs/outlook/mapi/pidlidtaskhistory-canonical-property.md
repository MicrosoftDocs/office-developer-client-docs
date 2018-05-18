---
title: "PidLidTaskHistory Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidTaskHistory
api_type:
- COM
ms.assetid: 104ef21c-b607-48b7-9b06-bc53b7d9b68a
description: "Last modified: March 09, 2015"
---

# PidLidTaskHistory Canonical Property

  
  
**Applies to**: Outlook 
  
Indicates the type of change that was last made to the task.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskHistory  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x0000811A  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

When the value of this property is set, the **dispidTaskLastUpdate** ([PidLidTaskLastUpdate](pidlidtasklastupdate-canonical-property.md)) property must also be set to the current time. The following table shows the **dispidTaskHistory** property values, listed in order of decreasing priority. 
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000004  <br/> |The **dispidTaskDueDate** ([PidLidTaskDueDate](pidlidtaskduedate-canonical-property.md)) property changed.  <br/> |
|0x00000003  <br/> |Another property was changed.  <br/> |
|0x00000001  <br/> |The task assignee accepted this task.  <br/> |
|0x00000002  <br/> |The task assignee rejected this task.  <br/> |
|0x00000005  <br/> |The task was assigned to a task assignee.  <br/> |
|0x00000000  <br/> |No changes were made.  <br/> |
   
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOTASK]](http://msdn.microsoft.com/library/55600ec0-6195-4730-8436-59c7931ef27e%28Office.15%29.aspx)
  
> Defines several objects that model the electronic equivalent of tasks, task assignments, and task updates.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

