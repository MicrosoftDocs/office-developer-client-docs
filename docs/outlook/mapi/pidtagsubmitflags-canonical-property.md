---
title: "PidTagSubmitFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagSubmitFlags
api_type:
- COM
ms.assetid: 9ea1c029-d53c-4c28-b413-560083b6215a
description: "Last modified: March 09, 2015"
---

# PidTagSubmitFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a bitmask of flags indicating details about a message submission.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SUBMIT_FLAGS  <br/> |
|Identifier:  <br/> |0x0E14  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI non-transmittable  <br/> |
   
## Remarks

One or more of the following flags can be set for the **PR_SUBMIT_FLAGS** bitmask: 
  
SUBMITFLAG_LOCKED 
  
> The MAPI spooler currently has the message locked. 
    
SUBMITFLAG_PREPROCESS 
  
> The message needs preprocessing. When the MAPI spooler is done preprocessing this message, it should call the [IMessage::SubmitMessage](imessage-submitmessage.md) method. The message store provider recognizes that the spooler, rather than the client application, has called **SubmitMessage**, clears the flag, and continues message submission.
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCICAL]](https://msdn.microsoft.com/library/a685a040-5b69-4c84-b084-795113fb4012%28Office.15%29.aspx)
  
> Converts between IETF RFC2445, RFC2446, and RFC2447, and appointment and meeting objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[IMsgStore::SetLockState](imsgstore-setlockstate.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

