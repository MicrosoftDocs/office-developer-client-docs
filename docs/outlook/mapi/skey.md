---
title: "SKEY"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 3f1e8291-6153-c308-94be-ca6745ea86a4
---

# SKEY

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Source key for an Outlook item.
  
## Quick info

```cpp
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



[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[UPDELE](updele.md)
  
[UPMSG](upmsg.md)
  
[UPREADE](upreade.md)

