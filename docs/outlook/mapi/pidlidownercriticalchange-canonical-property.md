---
title: "PidLidOwnerCriticalChange Canonical Property"
description: Outlines the PidLidOwnerCriticalChange canonical property, which specifies the date and time when a meeting request was sent by the organizer.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidOwnerCriticalChange
api_type:
- COM
ms.assetid: b79aa2b7-b6e0-46dc-89f1-f801a6b5737a
---

# PidLidOwnerCriticalChange Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the date and time when a meeting request was sent by the organizer.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |LID_OWNER_CRITICAL_CHANGE  <br/> |
|Property set:  <br/> |PSETID_Meeting  <br/> |
|Long ID (LID):  <br/> |0x0000001A  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

The value must be specified in Coordinated Universal Time (UTC).
  
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

