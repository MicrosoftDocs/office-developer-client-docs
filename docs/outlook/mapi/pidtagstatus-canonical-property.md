---
title: "PidTagStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagStatus
api_type:
- COM
ms.assetid: 8b947660-eafe-47e1-9595-bd3ab7d455bf
description: "Last modified: March 09, 2015"
---

# PidTagStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a 32-bit bitmask of flags that define folder status.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_STATUS  <br/> |
|Identifier:  <br/> |0x360B  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI container  <br/> |
   
## Remarks

This property for folders is analogous to the **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property for messages. Its flags are provided for the client application only and do not affect the message store. Clients can use or ignore these settings. The client can also define its own values for the client-definable bits of this property.
  
One or more of the following flags can be set for the bitmask:
  
FLDSTATUS_DELMARKED 
  
> The folder is marked for deletion. The client application sets this flag.
    
FLDSTATUS_HIDDEN 
  
> The folder is hidden.
    
FLDSTATUS_HIGHLIGHTED 
  
> The folder is highlighted, for example, shown in reverse video.
    
FLDSTATUS_TAGGED 
  
> The folder is tagged.
    
Message store providers set this property on a folder to one or more of these values and clients interpret the status as appropriate for their applications. For example, a client can use the folder status to visually differentiate between folders in a hierarchy table, displaying folders with the same status in the same way. Highlighted folders can be shown in reverse video, tagged folders and folders marked for deletion can be shown with a meaningful icon, and hidden folders can be concealed.
  
Bits 16 through 31 ("0x10000" through "0x80000000") of this property are available for use by the IPM client application. All other bits are reserved for use by MAPI; those not defined in the preceding list should be initially set to zero and not altered.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
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

