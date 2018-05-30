---
title: "PidLidTaskStartDate Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidTaskStartDate
api_type:
- COM
ms.assetid: fe87eb3d-21d1-45bb-b848-e141ce1be6a0
description: "Last modified: March 09, 2015"
---

# PidLidTaskStartDate Canonical Property

  
  
**Applies to**: Outlook 
  
The date when the user expects to begin the task.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskStartDate  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x00008104  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

If this property value is left unset, the task does not have a start date. A value of "0x5AE980E0" (1,525,252,320) also means that the task does not have a start date. If the task has a start date, the value must have a time component of midnight, and the **dispidTaskDueDate** ([PidLidTaskDueDate](pidlidtaskduedate-canonical-property.md)) and **dispidCommonStart** ([PidLidCommonStart](pidlidcommonstart-canonical-property.md)) properties must also be set.
  
This property is shared by the Informational Flagging Protocol Specification and Task-Related Object Protocol Specification located in [[MS-OXOTASK]](http://msdn.microsoft.com/library/55600ec0-6195-4730-8436-59c7931ef27e%28Office.15%29.aspx).
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOTASK]](http://msdn.microsoft.com/library/55600ec0-6195-4730-8436-59c7931ef27e%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on contacts and personal distribution lists.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[PidLidTaskDueDate Canonical Property](pidlidtaskduedate-canonical-property.md)
  
[PidLidCommonStart Canonical Property](pidlidcommonstart-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

