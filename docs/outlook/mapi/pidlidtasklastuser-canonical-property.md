---
title: "PidLidTaskLastUser Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidTaskLastUser
api_type:
- COM
ms.assetid: 914c55e9-cb36-46a4-b5ee-382413fa25f9
description: "Last modified: March 09, 2015"
---

# PidLidTaskLastUser Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Names the most recent user who was the task owner.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskLastUser  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x00008122  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

Before a client sends a task request, it sets this property to the name of the task assigner. Before a client sends a task acceptance, it sets this property to the name of the task assignee. Before a client sends a task rejection, it sets this property to the name of the task assigner.
  
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

