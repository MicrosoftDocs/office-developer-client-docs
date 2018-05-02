---
title: "MEID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa8f18d9-691d-d0cc-a660-f15ea6cff6ce
description: "Last modified: July 03, 2012"
---

# MEID

 **Last modified:** July 03, 2012 
  
 * **Applies to:** Outlook * 
  
Identifier for an Outlook item. It contains an entry identifier and other relevant information.
  
## Quick Info

```
struct MEID 
{ 
    BYTE abFlags[4]; 
    MAPIUID muid; 
    WORD placeholder; 
    LTID ltidFld; 
    LTID ltidMsg; 
};
```

## Members

 _abFlags_
  
> 4-byte entry identifier for the Outlook item. For more information about MAPI entry identifiers, see **[ENTRYID](entryid.md)**. 
    
 _muid_
  
> GUID that identifies the store provider. See mapidefs.h for the type definition of **MAPIUID**. 
    
 _placeholder_
  
> This member is reserved for the internal use of Outlook and is not supported.
    
 _ltidFld_
  
> Long-term ID of the folder.
    
 _ltidMsg_
  
> Long-term ID of the Outlook item.
    
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[LTID](ltid.md)
  
[SYNC](sync.md)
  
[UPMSG](upmsg.md)

