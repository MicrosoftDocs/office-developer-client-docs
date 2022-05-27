---
title: "PidTagExceptionReplaceTime Canonical Property"
description: Outlines the PidTagExceptionReplaceTime canonical property, which applies to Outlook 2013 and Outlook 2016.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagExceptionReplaceTime
api_type:
- HeaderDef
ms.assetid: bd4d1311-15e4-4275-a967-c6d11d2e48d2
---

# PidTagExceptionReplaceTime Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the original date and time when the instance in the recurrence pattern would have occurred if it were not an exception.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_EXCEPTION_REPLACETIME  <br/> |
|Identifier:  <br/> |0x7FF9  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Message class-defined non-transmittable  <br/> |
   
## Remarks

This value must be specified in Coordinated Universal Time (UTC).
  
## Related resources

### Protocol specifications

[[MS-OXOCAL]](https://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
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

