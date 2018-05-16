---
title: "PidLidAppointmentDuration Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidAppointmentDuration
api_type:
- COM
ms.assetid: 92c07a81-9dec-4118-af1f-02ecad340f07
description: "Last modified: March 09, 2015"
---

# PidLidAppointmentDuration Canonical Property

  
  
**Applies to**: Outlook 
  
Represents the length of time, in minutes, when an appointment is scheduled.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidApptDuration  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008213  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Calendar  <br/> |
   
## Remarks

The value must be the number of minutes between the value of the **dispidApptStartWhole** ( [PidLidAppointmentStartWhole](pidlidappointmentstartwhole-canonical-property.md)) and the **dispidApptEndWhole** ( [PidLidAppointmentEndWhole](pidlidappointmentendwhole-canonical-property.md)) properties.
  
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

