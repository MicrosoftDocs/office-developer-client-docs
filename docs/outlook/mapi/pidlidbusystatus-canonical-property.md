---
title: "PidLidBusyStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidBusyStatus
api_type:
- COM
ms.assetid: 50c91fe6-2a61-4348-a16d-fd5c501b0715
description: "Last modified: March 09, 2015"
---

# PidLidBusyStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Represents the user's availability for an appointment.
  
|Key |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidBusyStatus  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008205  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Calendar  <br/> |
   
## Remarks

This property specifies the availability of a user for the event described by the object and must be one of the values specified below.
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |The user is available. |
|0x00000001  <br/> |The user has a tentative event scheduled. |
|0x00000002  <br/> |The user is busy. |
|0x00000003  <br/> |The user is out of office. |
   
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

