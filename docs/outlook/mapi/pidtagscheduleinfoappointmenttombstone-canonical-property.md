---
title: "PidTagScheduleInfoAppointmentTombstone Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagScheduleInfoAppointmentTombstone
api_type:
- COM
ms.assetid: 6b82e2ee-992f-4cbe-bdcb-e7465e556640
description: "Last modified: March 09, 2015"
---

# PidTagScheduleInfoAppointmentTombstone Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a list of data blocks that represent meetings that have been declined.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SCHDINFO_APPT_TOMBSTONE  <br/> |
|Identifier:  <br/> |0x686A  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Free/Busy  <br/> |
   
## Remarks

The data blocks begin with a header of 32 bit values defined as:
  
|**Value**|**Description**|
|:-----|:-----|
|Identifier  <br/> |This field must be the value 0xBEDEAFCD.  <br/> |
|HeaderSize  <br/> |This field must have the value 0x00000014.  <br/> |
|Version  <br/> |This field must have the value 3.  <br/> |
|RecordsCount  <br/> |The count of records that follow.  <br/> |
|RecordsSize  <br/> |This field must have the value 0x00000014.  <br/> |
   
The header is followed by **RecordsCount** entries of 32 bit values defined as: 
  
|**Value**|**Description**|
|:-----|:-----|
|StartTime  <br/> |The meeting object's start time in minutes since midnight, January 1, 1601, UTC.  <br/> |
|EndTime  <br/> |The meeting object's end time in minutes since midnight, January 1, 1601, UTC.  <br/> |
|GlobalObjectIdSize  <br/> |The size, in bytes, of the GlobalObjectId field.  <br/> |
|GlobalObjectId  <br/> |The value of the **LID_GLOBAL_OBJID** ([PidLidGlobalObjectId](pidlidglobalobjectid-canonical-property.md)) property of the meeting this record represents.  <br/> |
|UserName  <br/> |The first two bytes are the length of the PT_STRING8 string that follows.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
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

