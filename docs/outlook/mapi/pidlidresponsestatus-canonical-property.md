---
title: "PidLidResponseStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidResponseStatus
api_type:
- COM
ms.assetid: e56142fd-204b-497e-83b9-59f9acda6cb4
description: "Specifies the response status of an attendee for Outlook 2013 or Outlook 2016."
---

# PidLidResponseStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the response status of an attendee.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidResponseStatus  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008218  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

The response status must be one of the values in the table below.
  
|**Response status**|**Value**|**Description**|
|:-----|:-----|:-----|
|respNone  <br/> |0x00000000  <br/> |No response is required for this object. This is the case for appointment objects and meeting response objects. |
|respOrganized  <br/> |0x00000001  <br/> |This meeting belongs to the organizer. |
|respTentative  <br/> |0x00000002  <br/> |This value on the attendee's meeting indicates that the attendee has tentatively accepted the meeting request. |
|respAccepted  <br/> |0x00000003  <br/> |This value on the attendee's meeting t indicates that the attendee has accepted the meeting request. |
|respDeclined  <br/> |0x00000004  <br/> |This value on the attendee's meeting indicates that the attendee has declined the meeting request. |
|respNotResponded  <br/> |0x00000005  <br/> |This value on the attendee's meeting indicates the attendee has not yet responded. This value is on the meeting request, meeting update, and meeting cancelation. |
   
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

