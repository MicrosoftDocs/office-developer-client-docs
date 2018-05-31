---
title: "PidTagRemoteProgress Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRemoteProgress
api_type:
- COM
ms.assetid: 01cae79e-5b56-4cd4-83a6-f0956ff539fb
description: "Last modified: March 09, 2015"
---

# PidTagRemoteProgress Canonical Property

  
  
**Applies to**: Outlook 
  
This property contains a number that indicates the status of a remote transfer.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_REMOTE_PROGRESS  <br/> |
|Identifier:  <br/> |0x3E0B  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI Status  <br/> |
   
## Remarks

If no transfer is in progress, this property should be set to 1. If a transfer is in progress, it should be set to a value from 0 to 100 indicating the transfer's percent of completion.
  
The text associated with the numeric status code appears in the **PR_REMOTE_PROGRESS_TEXT** ([PidTagRemoteProgressText](pidtagremoteprogresstext-canonical-property.md)) property.
  
The following flags can be set for this property:
  
MSGSTATUS_REMOTE_DELETE
  
> The message transfer is deleted.
    
MSGSTATUS_REMOTE_DOWNLOAD
  
> The message transfer is in progress.
    
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

