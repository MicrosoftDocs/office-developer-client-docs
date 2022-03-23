---
title: "PidLidTaskGlobalId Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidTaskGlobalId
api_type:
- COM
ms.assetid: 369d8c78-3cf6-4a55-ba14-9da0377d6ccf
description: "Locates an existing task, by using a GUID, upon receipt of a task response or task update. This property is left unset for unassigned tasks."
---

# PidLidTaskGlobalId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Locates an existing task, by using a GUID, upon receipt of a task response or task update.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskGlobalObjId  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008519  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

This property is left unset for unassigned tasks.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS] ](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
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

