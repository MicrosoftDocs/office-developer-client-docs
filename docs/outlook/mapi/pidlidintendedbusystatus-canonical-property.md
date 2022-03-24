---
title: "PidLidIntendedBusyStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidIntendedBusyStatus
api_type:
- COM
ms.assetid: 84221dd3-de71-4c10-abd7-9f15aefd02ed
description: "Last modified: March 09, 2015"
---

# PidLidIntendedBusyStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the value of the **dispidBusyStatus** ([PidLidBusyStatus](pidlidbusystatus-canonical-property.md)) property on the meeting in the organizer's calendar when the meeting request or meeting update was sent.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |dispidIntendedBusyStatus  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008224  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

The allowable values of this property are the same as those for the property **dispidBusyStatus**.
  
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

