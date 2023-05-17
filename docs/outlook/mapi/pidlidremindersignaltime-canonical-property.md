---
title: "PidLidReminderSignalTime Canonical Property"
description: Outlines the PidLidReminderSignalTime canonical property, which specifies the point in time when a reminder transitions from pending to overdue.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidReminderSignalTime
api_type:
- COM
ms.assetid: 58f6432e-6e88-420b-959f-7f365899f7eb
---

# PidLidReminderSignalTime Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the point in time when a reminder transitions from pending to overdue.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidReminderNextTime  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008560  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Reminder  <br/> |
   
## Remarks

This property must be set if the **dispidReminderSet** ([PidLidReminderSet](pidlidreminderset-canonical-property.md)) property is TRUE. Clients must set the value in Coordinated Universal Time (UTC).
  
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

