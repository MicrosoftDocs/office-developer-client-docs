---
title: "PidLidGlobalObjectId Canonical Property"
description: Outlines the PidLidGlobalObjectId canonical property, which specifies the unique identifier of the calendar object.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidGlobalObjectId
api_type:
- COM
ms.assetid: a4e3f9ab-b7ee-4dff-b7bd-2462c561735c
---

# PidLidGlobalObjectId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the unique identifier of the calendar object.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |LID_GLOBAL_OBJID  <br/> |
|Property set:  <br/> |PSETID_Meeting  <br/> |
|Long ID (LID):  <br/> |0x00000003  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

Once set for a calendar object, the value of this property must not change. A detailed description of the format can be found in [[MS-OXOCAL]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx).
  
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

