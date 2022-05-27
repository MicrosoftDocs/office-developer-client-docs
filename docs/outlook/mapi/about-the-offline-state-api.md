---
title: "About the Offline State API"
description: "Describes the Offline State API, which supports callbacks indicating changes in a user's connection state in Microsoft Outlook 2013 and 2010."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 18b0d284-c224-a022-47d9-b2d82a32f996
 
 
---

# About the Offline State API

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The Offline State API supports callbacks indicating changes in a user's connection state in Microsoft Outlook 2013 and Microsoft Outlook 2010—for example, from being online in Outlook 2013 or Outlook 2010 to being offline. The API uses a global offline object in Outlook 2013 or Outlook 2010 to track such changes for a given user account profile. Notification is the only supported form of callback. As clients of this API, mail providers who want to be notified of such connection state changes do the following:
  
1. Implement **[IMAPIOfflineNotify](imapiofflinenotifyiunknown.md)**. 
    
2. Open an existing offline object for a specific profile using **[HrOpenOfflineObj](hropenofflineobj.md)**. 
    
3. Determine if the object has the capability of providing online or offline notifications using **[IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)**. 
    
4. Register the object for online or offline notifications using **[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)**. Mail providers can now receive notifications that Outlook 2013 or Outlook 2010 send using **IMAPIOfflineNotify**. 
    
5. On shutdown, remove registration for online and offline notifications using **[IMAPIOfflineMgr::Unadvise](imapiofflinemgr-unadvise.md)**. 
    
> [!NOTE]
> In general, Outlook 2013 and Outlook 2010 can notify a client of online/offline changes as well as other changes, but the Offline State API supports only notifications for online/offline changes. The client should ignore all other notifications. For more information, see **[IMAPIOfflineNotify::Notify](imapiofflinenotify-notify.md)** and **[MAPIOFFLINE_NOTIFY](mapioffline_notify.md)**. 
  
 For an example of a client that uses the Offline State API, see [About the Sample Offline State Add-in](about-the-sample-offline-state-add-in.md). The Sample Offline State Add-in is a COM add-in that uses the Offline State API to monitor and change the connection state.
  
This API provides the following:
  
Definitions:
  
- [MAPI Constants](mapi-constants.md)
    
Data types:
  
- **[MAPIOFFLINE_ADVISEINFO](mapioffline_adviseinfo.md)**
    
- **[MAPIOFFLINE_CALLBACK_TYPE](mapioffline_callback_type.md)**
    
- **[MAPIOFFLINE_NOTIFY](mapioffline_notify.md)**
    
Functions:
  
- **[HrOpenOfflineObj](hropenofflineobj.md)**
    
Interfaces:
  
- **[IMAPIOffline](imapiofflineiunknown.md)**
    
- **[IMAPIOfflineMgr](imapiofflinemgrimapioffline.md)**
    
- **[IMAPIOfflineNotify](imapiofflinenotifyiunknown.md)**
    

