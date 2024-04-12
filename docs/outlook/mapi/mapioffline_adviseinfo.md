---
title: "MAPIOFFLINE_ADVISEINFO"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 20a46c69-d6ae-7d17-f8af-12952867d342
---

# MAPIOFFLINE_ADVISEINFO

**Applies to**: Outlook 2013 | Outlook 2016
  
Provides information to **[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)** to register callback for an offline object.
  
## Quick info

See **IMAPIOfflineMgr::Advise**.
  
```cpp
typedef struct 
{ 
      ULONG                   ulSize; 
      ULONG                   ulClientToken; 
      MAPIOFFLINE_CALLBACK_TYPE     CallbackType; 
      IUnknown*               pCallback; 
      ULONG                   ulAdviseTypes; 
      ULONG                   ulStateMask; 
} MAPIOFFLINE_ADVISEINFO;
```

## Members

_ulSize_: The size of **MAPIOFFLINE_ADVISEINFO**.

_ulClientToken_: A token defined by the client about a callback. It is the _ulClientToken_ member of the **[MAPIOFFLINE_NOTIFY](mapioffline_notify.md)** structure passed to **[IMAPIOfflineNotify::Notify](imapiofflinenotify-notify.md)**.

_CallbackType_: Type of callback to make.

- MAPIOFFLINE_CALLBACK_TYPE_NOTIFY

- The type of callback is by notification. This is the only supported type of callback. _pCallback_  must indicate the interface **[IMAPIOfflineNotify](imapiofflinenotifyiunknown.md)**.

_pCallback_: Interface to use for callback. This is the client's implementation of **[IMAPIOfflineNotify](imapiofflinenotifyiunknown.md)**.

_ulAdviseTypes_: The types of advise, as identified by the condition for advising. The only supported type is MAPIOFFLINE_ADVISE_TYPE_STATECHANGE.

_ulStateMask_: The only supported state is MAPIOFFLINE_STATE_ALL.

## See also

- [IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)
- [About the Offline State API](about-the-offline-state-api.md)
- [MAPI Constants](mapi-constants.md)
- [MAPIOFFLINE_CALLBACK_TYPE](mapioffline_callback_type.md)
