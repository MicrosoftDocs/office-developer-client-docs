---
title: "LTID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 17a412ba-3f74-ba94-0ffa-01dae63fc157
---

# LTID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Generic Long Term ID of an object in an Outlook store.
  
## Quick info

```cpp
struct LTID 
{ 
    GUID guid; 
    BYTE globcnt[6]; 
    WORD wLevel; 
};
```

## Members

 _guid_
  
- [out] The GUID of the server that created the object.
    
 _globcnt_
  
- [out] A 6-byte unique number that identifies the object within the Outlook store.
    
 _wLevel_
  
- [out] The hierarchy level of the entry ID for an Exchange Favorite Public folder.
    
## See also



[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[FEID](feid.md)

