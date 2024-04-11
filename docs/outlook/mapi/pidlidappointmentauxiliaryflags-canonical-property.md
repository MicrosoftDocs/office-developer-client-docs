---
title: "PidLidAppointmentAuxiliaryFlags Canonical Property"
description: "PidLidAppointmentAuxiliaryFlags Canonical Property specifies a bit field that describes the auxiliary state of the object."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidAppointmentAuxiliaryFlags
api_type:
- COM
ms.assetid: 56c64e23-4a99-4f80-ba06-dfae2a5fe961
---

# PidLidAppointmentAuxiliaryFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies a bit field that describes the auxiliary state of the object.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidApptAuxFlags  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008207  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

This property is not required. Below are the individual flags that can be set.
  
C (auxApptFlagCopied, 0x00000001)
  
> This flag indicates that the calendar object was copied from another calendar folder.
    
R (auxApptFlagForceMtgResponse, 0x00000002)
  
> This flag on a meeting request indicates that the client or server should send a meeting response back to the organizer when a response is chosen.
    
F (auxApptFlagForwarded, 0x00000004)
  
> This flag on a meeting request indicates that it was forwarded (including being forwarded by the organizer), rather than being an invitation from the organizer.
    
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

