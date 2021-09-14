---
title: "PidLidTaskAcceptanceState Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidTaskAcceptanceState
api_type:
- COM
ms.assetid: 7012f524-bc66-48ea-85b5-163e05029d35
description: "Last modified: March 09, 2015"
---

# PidLidTaskAcceptanceState Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the acceptance state of the task.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskDelegValue  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x0000812A  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

The following table shows the possible values for this property.
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |The task is not assigned.  <br/> |
|0x00000001  <br/> |The task's acceptance status is unknown.  <br/> |
|0x00000002  <br/> |The task assignee accepted the task. This value is set when the client processes a task acceptance.  <br/> |
|0x00000003  <br/> |The task assignee rejected the task. This value is set when the client processes a task rejection.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOTASK]](https://msdn.microsoft.com/library/55600ec0-6195-4730-8436-59c7931ef27e%28Office.15%29.aspx)
  
> Defines several objects that model the electronic equivalent of tasks, task assignments, and task updates.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

