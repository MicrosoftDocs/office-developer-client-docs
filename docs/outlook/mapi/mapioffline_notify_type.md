---
title: "MAPIOFFLINE_NOTIFY_TYPE"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a111d7b7-6e87-4958-8f9b-0f2adbeb8b63
description: "Last modified: July 23, 2011"
---

# MAPIOFFLINE_NOTIFY_TYPE

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The MAPIOFFLINE_NOTIFY_TYPE of a notification identifies if a change in the connection state is going to take place, is taking place, or has completed. 
  
## Quick info

See **[IMAPIOfflineNotify](imapiofflinenotifyiunknown.md)**. 
  
```cpp
typedef enum { 
    MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE_START = 1,  
    MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE = 2,  
    MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE_DONE = 3  
} MAPIOFFLINE_NOTIFY_TYPE;
```

## See also



[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[MAPIOFFLINE_NOTIFY](mapioffline_notify.md)

