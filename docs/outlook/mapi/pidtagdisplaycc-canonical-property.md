---
title: "PidTagDisplayCc Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDisplayCc
api_type:
- HeaderDef
ms.assetid: 00377e78-a208-4942-a7a6-893b2a71ab0b
description: "Last modified: March 09, 2015"
---

# PidTagDisplayCc Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an ASCII list of the display names of any carbon copy (CC) message recipients, separated by semicolons (;). 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_DISPLAY_CC, PR_DISPLAY_CC_A, PR_DISPLAY_CC_W  <br/> |
|Identifier:  <br/> |0x0E03  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |Message  <br/> |
   
## Remarks

The message store computes these properties on message objects by using the [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method. The message store also maintains these properties so that it always reflects the last saved state of a message. The value is synchronized at the time of every call to [IMAPIProp::SaveChanges](imapiprop-savechanges.md). 
  
If a message has no carbon copy recipients, the message store should respond to an [IMAPIProp::GetProps](imapiprop-getprops.md) call with a return value of S_OK and an empty string for these properties. 
  
Because of the possible need for localization, MAPI provides these guidelines for all recipient names:
  
- All names should be able to be localized. 
    
- The semicolon should be the character that is used to separate names in the **PR_DISPLAY_BCC** ([PidTagDisplayBcc](pidtagdisplaybcc-canonical-property.md)), **PR_DISPLAY_CC**, and **PR_DISPLAY_TO** ([PidTagDisplayTo](pidtagdisplayto-canonical-property.md)) properties. Semicolons are not permitted within recipient names in MAPI. 
    
- Clients should translate each semicolon encountered in this property to a localized separator character before making the property information visible in the user interface. 
    
- When forwarding messages, clients do not need to translate the separator characters on the carbon copy recipient line. 
    
## Related resources

### Protocol specifications

[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
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

