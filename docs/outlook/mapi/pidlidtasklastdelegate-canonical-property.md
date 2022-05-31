---
title: "PidLidTaskLastDelegate Canonical Property"
description: Outlines the PidLidTaskLastDelegate canonical property, which names the user who most recently assigned or was assigned the task. 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidTaskLastDelegate
api_type:
- COM
ms.assetid: 5eb8c1ce-063f-4273-acba-e6f9c994e7d3
---

# PidLidTaskLastDelegate Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 Names the user who most recently assigned or was assigned the task. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskLastDelegate  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x00008125  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

Before sending a task request, the client sets this property to the name of the task assigner. Before sending a task response, the client sets this property to the name of the task assignee.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definition and references to related Exchange Server protocol specifications.
    
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

