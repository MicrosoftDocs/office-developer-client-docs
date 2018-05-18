---
title: "PidTagFreeBusyCountMonths Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFreeBusyCountMonths
api_type:
- HeaderDef
ms.assetid: 278a77f2-65ec-4281-b406-942cc416a476
description: "Last modified: March 09, 2015"
---

# PidTagFreeBusyCountMonths Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the value for calculating the start and end dates of the range of free/busy data to be published to public folders.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FREEBUSY_COUNT_MONTHS  <br/> |
|Identifier:  <br/> |0x6869  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Message class-defined transmittable  <br/> |
   
## Remarks

This property's value must be greater than or equal to 0 and less than or equal to 36. This is not a required property.
  
## Related resources

### Protocol specifications

[[MS-OXOPFFB]](http://msdn.microsoft.com/library/1a527299-7211-4d27-a74c-b69bd0746320%28Office.15%29.aspx)
  
> Publishes the availability of a user or resource.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

