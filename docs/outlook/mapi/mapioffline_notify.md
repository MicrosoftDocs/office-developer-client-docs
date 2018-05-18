---
title: "MAPIOFFLINE_NOTIFY"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e03c5a87-4513-2133-ae0a-11d242f80e4b
description: "Last modified: July 23, 2011"
---

# MAPIOFFLINE_NOTIFY

  
  
**Applies to**: Outlook 
  
This is the notification for a change in the connection state. It indicates the part of the connection state that has changed, the old connection state, and the new connection state.
  
## Quick info

See **[IMAPIOfflineNotify](imapiofflinenotifyiunknown.md)**. 
  
```cpp
typedef struct  
{ 
      ULONG ulSize; 
      MAPIOFFLINE_NOTIFY_TYPE NotifyType; 
      ULONG ulClientToken; 
      union { 
         struct 
           { 
           ULONG ulMask; 
           ULONG ulStateOld; 
           ULONG ulStateNew; 
           } StateChange; 
             } Info; 
} MAPIOFFLINE_NOTIFY;
```

## Members

 _ulSize_
  
> Size of the **MAPIOFFLINE_NOTIFY** structure. 
    
 _NotifyType_
  
> Type of notification. Note that only notification on change of the connection state is supported; the only supported values are:
    
    - MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE_START
    
    - MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE
    
    - MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE_DONE
    
 _ulClientToken_
  
> A token defined by the client in the **[MAPIOFFLINE_ADVISEINFO](mapioffline_adviseinfo.md)** structure in **[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)**. 
    
 _ulMask_
  
> The part of the connection state that has changed. The only supported value is MAPIOFFLINE_STATE_OFFLINE_MASK.
    
 _ulStateOld_
  
> The old connection state. The only supported values are:
    
    - MAPIOFFLINE_STATE_OFFLINE
    
    - MAPIOFFLINE_STATE_ONLINE
    
 _ulStateNew_
  
> The new connection state. The only supported values are:
    
    - MAPIOFFLINE_STATE_OFFLINE
    
    - MAPIOFFLINE_STATE_ONLINE
    
## Remarks

The Offline State API supports only notifications for online/offline changes. A client must check that Outlook returns the following values before examining the actual change:
  
1.  *NotifyType*  has the value MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE_START, MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE, or MAPIOFFLINE_NOTIFY_TYPE_STATECHANGE_DONE. In this case, the client can assume that the change is a connection state change, and  *Info*  is of the structure  *StateChange*  . 
    
2.  *ulMask*  has the value MAPIOFFLINE_STATE_OFFLINE_MASK. In this case, the client can assume that the change is an online/offline connection state change, and can proceed with examining  *ulStateOld*  and  *ulStateNew*  . 
    
 It is possible that Outlook notifies a client of other changes that are not supported. In such cases,  *NotifyType*  would not be any one of the three values stated previously, or  *ulMask*  would not be MAPIOFFLINE_STATE_OFFLINE_MASK, and the client must ignore the rest of the data in  *Info*  . 
  
## See also



[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[MAPIOFFLINE_NOTIFY_TYPE](mapioffline_notify_type.md)

