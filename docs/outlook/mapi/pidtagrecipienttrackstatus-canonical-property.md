---
title: "PidTagRecipientTrackStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRecipientTrackStatus
api_type:
- COM
ms.assetid: d619b5e7-2867-44fc-9b42-123bb1bf7bde
description: "Last modified: March 09, 2015"
---

# PidTagRecipientTrackStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the response status returned by the attendee.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RECIPIENT_TRACKSTATUS  <br/> |
|Identifier:  <br/> |0x5FFF  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Transport recipient  <br/> |
   
## Remarks

If this value is not set, it must be assumed to be respNone. Otherwise, it must be one of the following:
  
|**Response status**|**Value**|**Description**|
|:-----|:-----|:-----|
|respNone  <br/> |0x00000000  <br/> |No response is required for this object. This is the case for appointment objects and meeting response objects.  <br/> |
|respTentative  <br/> |0x00000002  <br/> |This value on the attendee's meeting object indicates that the attendee has tentatively accepted the meeting request object.  <br/> |
|respAccepted  <br/> |0x00000003  <br/> |This value on the attendee's meeting object indicates that the attendee has accepted the meeting request object.  <br/> |
|respDeclined  <br/> |0x00000004  <br/> |This value on the attendee's meeting object indicates that the attendee has declined the meeting request object.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](https://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

