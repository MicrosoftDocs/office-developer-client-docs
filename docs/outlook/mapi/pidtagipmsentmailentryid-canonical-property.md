---
title: "PidTagIpmSentMailEntryId Canonical Property"
description: Outlines the PidTagIpmSentMailEntryId canonical property, which contains the entry identifier of the standard interpersonal message (IPM) Sent Items folder.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagIpmSentMailEntryId
api_type:
- HeaderDef
ms.assetid: f6877435-6b26-4060-924f-a65591ad9538
---

# PidTagIpmSentMailEntryId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the entry identifier of the standard interpersonal message (IPM) Sent Items folder. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_IPM_SENTMAIL_ENTRYID  <br/> |
|Identifier:  <br/> |0x35E4  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Folder  <br/> |
   
## Remarks

After being sent, interpersonal messages are usually placed in the Sent Items folder. A client can use this property to set the **PR_SENTMAIL_ENTRYID** ([PidTagSentMailEntryId](pidtagsentmailentryid-canonical-property.md)) property on a submitted message. 
  
## Related resources

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

