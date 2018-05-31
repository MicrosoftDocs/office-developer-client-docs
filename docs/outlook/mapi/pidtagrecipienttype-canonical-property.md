---
title: "PidTagRecipientType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRecipientType
api_type:
- COM
ms.assetid: 67e31027-6bc2-4a40-9b00-d61baef4ab0f
description: "Last modified: March 09, 2015"
---

# PidTagRecipientType Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the recipient type for a message recipient.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RECIPIENT_TYPE  <br/> |
|Identifier:  <br/> |0x0C15  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI recipient  <br/> |
   
## Remarks

The recipient type contained in this property consists of one required value and one optional flag.
  
This property must contain exactly one of the following values:
  
MAPI_TO 
  
> The recipient is a primary (To) recipient. Clients are required to handle primary recipients. All other types are optional.
    
MAPI_CC 
  
> The recipient is a carbon copy (CC) recipient, a recipient that receives a message in addition to the primary recipients.
    
MAPI_BCC 
  
> The recipient is a blind carbon copy (BCC) recipient. Primary and carbon copy recipients are unaware of the existence of BCC recipients. 
    
MAPI_P1 
  
> The recipient did not successfully receive the message on the previous attempt. This is a resend of an earlier transmission.
    
In addition, the following flag can be set:
  
MAPI_SUBMITTED 
  
> The recipient has already received the message and does not need to receive it again. This is a resend of an earlier transmission. This flag is set in conjunction with the **MAPI_TO**, **MAPI_CC**, and **MAPI_BCC** values. 
    
The MAPI_P1 value and the **MAPI_SUBMITTED** flag are used when a message is being retransmitted due to nondelivery to one or more of the intended recipients. For this retransmission, the client sets **MAPI_SUBMITTED** on every recipient that does not need the message again but should be displayed in the recipient list. For every recipient that did not receive the message previously, the client retains the original recipient with its **PR_RECIPIENT_TYPE** value unchanged, but additionally submits a copy of the recipient with MAPI_P1 in place of the original value. This copy, which is discarded before actual delivery, forces the recipient into the P1 envelope and guarantees physical retransmission to that recipient. The **PR_RESPONSIBILITY** ([PidTagResponsibility](pidtagresponsibility-canonical-property.md)) property is set to FALSE for MAPI_P1 recipients.
  
When a client displays a resend form, only the MAPI_P1 recipients are visible. Unless the user enters additional recipients, when the message is delivered, the recipient list appears exactly as it did when the message was sent for the first time. 
  
The **PR_DISPLAY_TO** ([PidTagDisplayTo](pidtagdisplayto-canonical-property.md)), **PR_DISPLAY_CC** ([PidTagDisplayCc](pidtagdisplaycc-canonical-property.md)) and **PR_DISPLAY_BCC** ([PidTagDisplayBcc](pidtagdisplaybcc-canonical-property.md)) properties are related to recipient type. When a client calls a message's **IMAPIProp::SaveChanges** and there is at least one recipient in the recipient list, the message store provider sets these properties as follows: 
  
|**Property**|**Description**|
|:-----|:-----|
|PR_DISPLAY_TO  <br/> |Set to TRUE if one or more of the recipients are **MAPI_TO** recipients.  <br/> |
|PR_DISPLAY_CC  <br/> |Set to TRUE if one or more of the recipients are **MAPI_CC** recipients.  <br/> |
| PR_DISPLAY_BCC  <br/> |Set to TRUE if one or more of the recipients are **MAPI_BCC** recipients.  <br/> |
   
In X.400, the P1 or delivery envelope is the information needed to deliver a message, including the recipient's address properties and any option flags controlling delivery and replies. The P2 or display envelope is the information usually displayed to each recipient other than the message text itself. It typically includes the subject, importance, priority, sensitivity, and submission time, as well as the primary and copied recipient names. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagRecipientStatus Canonical Property](pidtagrecipientstatus-canonical-property.md)
  
[PidTagDisplayTo Canonical Property](pidtagdisplayto-canonical-property.md)
  
[PidTagDisplayBcc Canonical Property](pidtagdisplaybcc-canonical-property.md)
  
[PidTagDisplayCc Canonical Property](pidtagdisplaycc-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

