---
title: "IMAPIOfflineNotifyNotify"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOfflineNotify.Notify
api_type:
- COM
ms.assetid: 10c7cb9d-2e9d-72eb-6b07-31eed892e646
description: "Last modified: June 25, 2012"
---

# IMAPIOfflineNotify::Notify

 **Last modified:** June 25, 2012 
  
 * **Applies to:** Outlook * 
  
Sends notifications to the client about changes in connection state.
  
```
void STDMETHODCALLTYPE Notify(  
    const MAPIOFFLINE_NOTIFY * pNotifyInfo 
);
```

## Parameters

 _pNotifyInfo_
  
> [in] The notification that Outlook sends to the client. The notification indicates the part of the connection state that has changed, the old connection state, and the new connection state.
    
## Remarks

Outlook uses this method to send notification callbacks to a client. To make this interface available to Microsoft Outlook 2010 or Microsoft Outlook 2013, the client must implement this interface and pass a pointer to it as a member in **[MAPIOFFLINE_ADVISEINFO](mapioffline_adviseinfo.md)** when setting up callbacks using **[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)**. 
  
The client also passes to **MAPIOFFLINE_ADVISEINFO** a client token that Outlook 2010 or Outlook 2013 uses in **IMAPIOfflineNotify::Notify** to identify the client registered for the notification callback. 
  
In general, Outlook 2010 and Outlook 2013 can notify a client of online/offline changes and other connection state changes, but the Offline State API supports only notifications for online/offline changes. The client must ignore all other notifications.
  
## See also

#### Concepts

[About the Offline State API](about-the-offline-state-api.md)
  
[MAPIOFFLINE_NOTIFY](mapioffline_notify.md)

