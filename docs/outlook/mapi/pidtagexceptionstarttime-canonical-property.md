---
title: "PidTagExceptionStartTime Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagExceptionStartTime
api_type:
- HeaderDef
ms.assetid: 3aa4f9d7-8105-435d-af68-424a079e1a84
description: "Last modified: March 09, 2015"
---

# PidTagExceptionStartTime Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Indicates the start date and time of the exception in the local time zone of the machine when the exception is created.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EXCEPTION_STARTTIME  <br/> |
|Identifier:  <br/> |0x7FFB  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Message class-defined non-transmittable  <br/> |
   
## Remarks

> [!NOTE]
> This property is informational and must not be relied on for critical information. 
  
## Related Resources

### Protocol Specifications

[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

