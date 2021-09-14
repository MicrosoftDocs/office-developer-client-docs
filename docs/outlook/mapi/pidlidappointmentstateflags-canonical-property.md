---
title: "PidLidAppointmentStateFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidAppointmentStateFlags
api_type:
- COM
ms.assetid: 1e5f0f83-c40b-4b3a-8492-61d1b53b1e3c
description: "Last modified: March 09, 2015"
---

# PidLidAppointmentStateFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies a bit field that describes the state of the object.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidApptStateFlags  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008217  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

This property is not required. Below are the individual flags that can be set.
  
M (asfMeeting, 0x00000001)
  
> This flag indicates that the object is a meeting object or a meeting-related object.
    
R (asfReceived, 0x00000002)
  
> This flag indicates that the represented object was received from someone else.
    
C (asfCanceled, 0x00000004)
  
> This flag indicates that the meeting object represented by the object has been canceled.
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](https://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

