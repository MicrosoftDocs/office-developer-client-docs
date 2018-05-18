---
title: "IMAPIOfflineNotify  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOfflineNotify
api_type:
- COM
ms.assetid: a593d2a1-29f8-7e23-85bf-02fa3cfebe1b
description: "Last modified: March 09, 2015"
---

# IMAPIOfflineNotify : IUnknown

  
  
**Applies to**: Outlook 
  
Supports Microsoft Outlook 2010 and Microsoft Outlook 2013 in sending notification callbacks to a client.
  
|||
|:-----|:-----|
|Provided by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IMAPIOfflineNotify  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[Notify](imapiofflinenotify-notify.md) <br/> |Sends notifications to a client about changes in connection state.  <br/> |
   
## Remarks

The client must implement this interface and pass a pointer to it as a member in **[MAPIOFFLINE_ADVISEINFO](mapioffline_adviseinfo.md)** when setting up callbacks using **[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)**. Subsequently, Outlook 2010 or Outlook 2013 will be able to use this interface to send notification callbacks to the client. 
  
## See also



[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)


[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[MAPIOFFLINE_ADVISEINFO](mapioffline_adviseinfo.md)

