---
title: "PidLidOriginalStoreEntryId Canonical Property"
description: Outlines the PidLidOriginalStoreEntryId canonical property, which specifies the entry ID of the delegator's store.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidOriginalStoreEntryId
api_type:
- COM
ms.assetid: 1b1fc008-9cd5-49f6-9f91-b59e305a1e82
---

# PidLidOriginalStoreEntryId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the entry ID of the delegator's store.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidOrigStoreEid  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008237  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

This property should be set on meeting objects which have been created or updated by a delegate.
  
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

