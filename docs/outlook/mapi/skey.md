---
title: "SKEY"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f1e8291-6153-c308-94be-ca6745ea86a4
description: "Last modified: July 23, 2011"
---

# SKEY

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Source key for an Outlook item.
  
## Quick Info

```
struct SKEY 
{ 
    GUID guid; 
    BYTE globcnt[6]; 
};
```

## Members

 _guid_
  
> GUID of the server creating the object.
    
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[UPDELE](updele.md)
  
[UPMSG](upmsg.md)
  
[UPREADE](upreade.md)

