---
title: "INDEX_SEARCH_PUSHER_PROCESS"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 6b39504f-6eed-2605-048d-2707f38a7d9a
description: "Last modified: July 23, 2011"
---

# INDEX_SEARCH_PUSHER_PROCESS

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the process that is sending a notification to the MAPI Protocol Handler that an object in that store is ready for indexing.
  
## Quick info

```cpp
typedef struct _INDEX_SEARCH_PUSHER_PROCESS {  
    DWORD dwPID;  
} INDEX_SEARCH_PUSHER_PROCESS; 
```

## Members

 *dwPID* 
  
>  Process ID for the process that is sending an indexing notification to the indexer of the MAPI Protocol Handler. 
    

