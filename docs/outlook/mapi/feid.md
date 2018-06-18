---
title: "FEID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2dde7eec-df3d-723c-db08-7ff0b6107a0b
description: "Last modified: July 02, 2012"
---

# FEID

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Identifier for a folder. It contains an entry identifier and other relevant information.
  
## Quick info

```cpp
struct FEID 
{ 
    BYTE abFlags[4]; 
    MAPIUID muid; 
    WORD placeholder; 
    LTID ltid; 
};
```

## Members

 _abFlags_
  
> 4-byte entry identifier for the folder. For more information about MAPI entry identifiers, see **[ENTRYID](entryid.md)**. 
    
 _muid_
  
> GUID that identifies the store provider. See mapidefs.h for the type definition of **MAPIUID**. 
    
 _placeholder_
  
> This member is reserved for the internal use of Outlook and is not supported.
    
 _ltid_
  
> Long-term ID of the folder.
    
## See also



[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)
  
[LTID](ltid.md)
  
[UPFLD](upfld.md)
  
[SYNC](sync.md)

