---
title: "PidTagRemoteProgressText Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRemoteProgressText
api_type:
- COM
ms.assetid: b74d4350-4ad6-4c3f-8326-bd28537dfa0f
description: "Last modified: March 09, 2015"
---

# PidTagRemoteProgressText Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This property contains a string that indicates the status of a remote transfer.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_REMOTE_PROGRESS_TEXT, PR_REMOTE_PROGRESS_TEXT_A, PR_REMOTE_PROGRESS_TEXT_W  <br/> |
|Identifier:  <br/> |0x3E0C  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI Status  <br/> |
   
## Remarks

A numeric code associated with this text is passed in the **PR_REMOTE_PROGRESS** ([PidTagRemoteProgress](pidtagremoteprogress-canonical-property.md)) property.
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

