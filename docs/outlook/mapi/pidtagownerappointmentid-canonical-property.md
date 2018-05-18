---
title: "PidTagOwnerAppointmentId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOwnerAppointmentId
api_type:
- COM
ms.assetid: b5eea554-6bca-42d1-b943-1327f0d70584
description: "Last modified: March 09, 2015"
---

# PidTagOwnerAppointmentId Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an identifier for an appointment in the owner's schedule.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_OWNER_APPT_ID  <br/> |
|Identifier:  <br/> |0x0062  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Appointment  <br/> |
   
## Remarks

This property is used in meeting requests. It does not represent an entry identifier, but a long integer that uniquely identifies the appointment within the sender's schedule.
  
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
[[MS-OXCICAL]](http://msdn.microsoft.com/library/a685a040-5b69-4c84-b084-795113fb4012%28Office.15%29.aspx)
  
> Converts between IETF RFC2445, RFC2446, and RFC2447, and appointment and meeting objects.
    
[[MS-OXTNEF]](http://msdn.microsoft.com/library/1f0544d7-30b7-4194-b58f-adc82f3763bb%28Office.15%29.aspx)
  
> Encodes and decodes message and attachment objects to an efficient stream representation.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[PidTagOriginalAuthorSearchKey Canonical Property](pidtagoriginalauthorsearchkey-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

