---
title: "PidTagRecipientFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRecipientFlags
api_type:
- COM
ms.assetid: 9fbe537f-b5fe-48a2-803c-653c50c82efd
description: "Specifies a bit field that describes the recipient status. This property is not required."
---

# PidTagRecipientFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies a bit field that describes the recipient status.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RECIPIENT_FLAGS  <br/> |
|Identifier:  <br/> |0x5FFD  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Transport recipient  <br/> |
   
## Remarks

This property is not required. The following are the individual flags that can be set.
  
|**Value**|**Description**|
|:-----|:-----|
|S (recipSendable, 0x00000001)  <br/> |The recipient is a **Sendable** Attendee. This flag is only used in the **dispidApptUnsendableRecips** ([PidLidAppointmentUnsendableRecipients](pidlidappointmentunsendablerecipients-canonical-property.md)) property. |
|O (recipOrganizer, 0x0000002)  <br/> |The **RecipientRow** on which this flag is set represents the meeting Organizer. |
|ER (recipExceptionalResponse, 0x00000010)  <br/> |Indicates that the attendee gave a response for the exception on which this **RecipientRow** resides. This flag is only used in a **RecipientRow** of an exception embedded message object of the organizer's meeting object. |
|ED (recipExceptionalDeleted, 0x00000020)  <br/> |Indicates that although the **RecipientRow** exists, it should be treated as if the corresponding recipient does not. This flag is only used in a **RecipientRow** of an exception embedded message object of the organizer's meeting object. |
|X (reserved, 0x00000040)  <br/> |Must not be set. |
|X (reserved, 0x00000080)  <br/> |Must not be set. |
|G (recipOriginal, 0x00000100)  <br/> |Indicates the recipient is an original attendee. This flag is only used in the **dispidApptUnsendableRecips** property. |
|X (reserved, 0x00000200)  <br/> |Reserved. |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
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

