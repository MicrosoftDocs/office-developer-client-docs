---
title: "IMAPIOfflineNotify  IUnknown"
description: "IMAPIOfflineNotifyIUnknown supports Microsoft Outlook 2010 and Microsoft Outlook 2013 in sending notification callbacks to a client."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIOfflineNotify
api_type:
- COM
ms.assetid: a593d2a1-29f8-7e23-85bf-02fa3cfebe1b
---

# IMAPIOfflineNotify : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Supports Microsoft Outlook 2010 and Microsoft Outlook 2013 in sending notification callbacks to a client.
  
|Property|Descrption|
|:-----|:-----|
|Provided by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IMAPIOfflineNotify  <br/> |
   
## Vtable order

|Member|Description|
|:-----|:-----|
|[Notify](imapiofflinenotify-notify.md) <br/> |Sends notifications to a client about changes in connection state. |
   
## Remarks

The client must implement this interface and pass a pointer to it as a member in **[MAPIOFFLINE_ADVISEINFO](mapioffline_adviseinfo.md)** when setting up callbacks using **[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)**. Subsequently, Outlook 2010 or Outlook 2013 will be able to use this interface to send notification callbacks to the client. 
  
## See also



[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)


[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[MAPIOFFLINE_ADVISEINFO](mapioffline_adviseinfo.md)

