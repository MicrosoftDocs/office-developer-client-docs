---
title: "PidLidMeetingType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidMeetingType
api_type:
- COM
ms.assetid: 290b290c-7836-4a7e-bf1a-8d0225a07e56
description: "Last modified: March 09, 2015"
---

# PidLidMeetingType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the type of meeting request or meeting update.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidMeetingType  <br/> |
|Property set:  <br/> |PSETID_Meeting  <br/> |
|Long ID (LID):  <br/> |0x00000026  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

The value of this property must be set to one of the following:
  
|**Property**|**Value**|**Description**|
|:-----|:-----|:-----|
|mtgEmpty  <br/> |0x00000000  <br/> |Unspecified. |
|mtgRequest  <br/> |0x00000001  <br/> |Initial meeting request. |
|mtgFull  <br/> |0x00010000  <br/> |Full update. |
|mtgInfo  <br/> |0x00020000  <br/> |Informational update. |
|mtgOutOfDate  <br/> |0x00080000  <br/> |A newer meeting request or meeting update was received after this one. |
|mtgDelegatorCopy  <br/> |0x00100000  <br/> |This is set on the delegator's copy when a delegate handles meeting-related objects. |
   
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

