---
title: "PidLidReminderDelta Canonical Property"
description: Outlines the PidLidReminderDelta canonical property, which specifies an interval in minutes and applies to Outlook 2013 and Outlook 2016.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidReminderDelta
api_type:
- COM
ms.assetid: 011d73d0-8b38-4a4e-a56f-92dec451946a
---

# PidLidReminderDelta Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the interval, in minutes, between the time when the reminder first becomes overdue and the start time of the calendar object.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidReminderDelta  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008501  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Reminder  <br/> |
   
## Remarks

This property must be set on calendar objects. For all non-calendar objects, this property should be set to "0x00000000" and is ignored. When a reminder is dismissed for one instance of a recurring calendar object, the value of this property is used in the calculation of the signal time for the next instance. See [[MS- OXOCAL]](https://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx) for details about calendar object creation. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXORMDR]](https://msdn.microsoft.com/library/5454ebcc-e5d1-4da8-a598-d393b101caab%28Office.15%29.aspx)
  
> Specifies the properties and the interaction model for email and other object reminders.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

