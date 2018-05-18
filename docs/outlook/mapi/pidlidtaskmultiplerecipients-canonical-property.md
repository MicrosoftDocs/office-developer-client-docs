---
title: "PidLidTaskMultipleRecipients Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidTaskMultipleRecipients
api_type:
- COM
ms.assetid: 28ba9997-72dd-465f-94a7-35a317a361ef
description: "Last modified: March 09, 2015"
---

# PidLidTaskMultipleRecipients Canonical Property

  
  
**Applies to**: Outlook 
  
Provides optimization hints about the recipients of a task.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidTaskMultRecips  <br/> |
|Property set:  <br/> |PSETID_Task  <br/> |
|Long ID (LID):  <br/> |0x00008120  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

If set, this property must be set to a bitwise **OR** operation of zero or more of the following values. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|Sent  <br/> |0x00000001  <br/> |The task has multiple primary recipients.  <br/> |
|Received  <br/> |0x00000002  <br/> |Although the Sent hint was not present, the client detected that the task has multiple primary recipients.  <br/> |
|Reserved  <br/> |0x00000004  <br/> |This value is reserved.  <br/> |
   
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

