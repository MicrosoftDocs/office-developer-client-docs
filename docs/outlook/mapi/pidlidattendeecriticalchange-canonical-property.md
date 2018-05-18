---
title: "PidLidAttendeeCriticalChange Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidAttendeeCriticalChange
api_type:
- COM
ms.assetid: 2b46966d-c63d-4241-92d4-001d6a674e97
description: "Last modified: March 09, 2015"
---

# PidLidAttendeeCriticalChange Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the date and time when the meeting-related object was sent.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |LID_ATTENDEE_CRITICAL_CHANGE  <br/> |
|Property set:  <br/> |PSETID_Meeting  <br/> |
|Long ID (LID):  <br/> |0x00000001  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

The value must be specified in Coordinated Universal Time (UTC).
  
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

