---
title: "PidLidTaskVersion Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidTaskVersion
api_type:
- COM
ms.assetid: 3ab77f25-ad11-4501-8d35-ef560c07e2f2
description: "Last modified: March 09, 2015"
---

# PidLidTaskVersion Canonical Property

  
  
**Applies to**: Outlook 
  
Indicates which copy is the latest update of a task.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskVersion  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x00008112  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

Updates with lower versions than the task are ignored. 
  
When embedding a task in a task communication, the client sets the current version of the embedded task on the task communication as well.
  
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

