---
title: "UPREAD"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 568f2336-cb4d-3f2c-a304-d29cdb0bcbcc
description: "Last modified: July 23, 2011"
---

# UPREAD

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Information for uploading the read state of items during the [upload read status state](upload-read-status-state.md).
  
## Quick Info

```
struct UPREAD 
{ 
    PUPREADE pupre; 
    UINT cEnt; 
};
```

## Members

 _pupre_
  
>  [out] Vector of **[UPREADE](upreade.md)** entries. 
    
 _cEnt_
  
>  [out] Number of **UPREADE** entries. 
    
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)
  
[UPREADE](upreade.md)

