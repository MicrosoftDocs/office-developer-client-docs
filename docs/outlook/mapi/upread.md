---
title: "UPREAD"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 568f2336-cb4d-3f2c-a304-d29cdb0bcbcc
description: "Last modified: July 23, 2011"
---

# UPREAD

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Information for uploading the read state of items during the [upload read status state](upload-read-status-state.md).
  
## Quick info

```cpp
struct UPREAD 
{ 
    PUPREADE pupre; 
    UINT cEnt; 
};
```

## Members

 _pupre_
  
> [out] Vector of **[UPREADE](upreade.md)** entries. 
    
 _cEnt_
  
> [out] Number of **UPREADE** entries. 
    
## See also



[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)
  
[UPREADE](upreade.md)

