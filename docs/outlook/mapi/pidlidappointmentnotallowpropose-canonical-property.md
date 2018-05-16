---
title: "PidLidAppointmentNotAllowPropose Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidAppointmentNotAllowPropose
api_type:
- COM
ms.assetid: 8be9e2aa-2dc1-406d-8864-7f556de22809
description: "Last modified: March 09, 2015"
---

# PidLidAppointmentNotAllowPropose Canonical Property

  
  
**Applies to**: Outlook 
  
Indicates whether attendees are not allowed to propose a new date/time for the meeting.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidApptNotAllowPropose  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x0000825A  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

A value of FALSE, or the absence of this property indicates that the attendees are allowed to propose a new date/time.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

