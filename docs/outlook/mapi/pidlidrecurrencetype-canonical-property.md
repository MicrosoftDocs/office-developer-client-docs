---
title: "PidLidRecurrenceType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidRecurrenceType
api_type:
- COM
ms.assetid: 81ad2e8a-661f-4fc7-bee4-848db3285e31
description: "Last modified: March 09, 2015"
---

# PidLidRecurrenceType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the recurrence type of the recurring series.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidRecurType  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008231  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Calendar  <br/> |
   
## Remarks

This property specifies the recurrence type of the recurring series by using one of the values listed below.
  
|**Status**|**Value**|**Description**|
|:-----|:-----|:-----|
|rectypeNone  <br/> |0  <br/> |A single instance appointment.  <br/> |
|rectypeDaily  <br/> |1  <br/> |A daily recurrence pattern.  <br/> |
|rectypeWeekly  <br/> |2  <br/> |A weekly recurrence pattern.  <br/> |
|rectypeMonthly  <br/> |3  <br/> |A monthly recurrence pattern.  <br/> |
|rectypeYearly  <br/> |4  <br/> |A yearly recurrence pattern.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

