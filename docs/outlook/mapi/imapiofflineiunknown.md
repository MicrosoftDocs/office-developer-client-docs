---
title: "IMAPIOffline  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOffline
api_type:
- COM
ms.assetid: 211281ff-3c22-1b51-4b72-ca1e313c7202
description: "Last modified: March 09, 2015"
---

# IMAPIOffline : IUnknown

  
  
**Applies to**: Outlook 
  
Provides information for an offline object.
  
|||
|:-----|:-----|
|Provided by:  <br/> |Query on [IMAPIOfflineMgr](imapiofflinemgrimapioffline.md) <br/> |
|Called by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IMAPIOffline  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|**[SetCurrentState](imapioffline-setcurrentstate.md)** <br/> |Sets the current state of an offline object to online or offline.  <br/> |
|**[GetCapabilities](imapioffline-getcapabilities.md)** <br/> |Gets the conditions for which callbacks are supported by an offline object.  <br/> |
|**[GetCurrentState](imapioffline-getcurrentstate.md)** <br/> |Gets the current online or offline state of an offline object.  <br/> |
| *Placeholder member*  <br/> |This member is a placeholder and is not supported.  <br/> |
   
## Remarks

A client uses **[HrOpenOfflineObj](hropenofflineobj.md)** to open and obtain an offline object that supports **IMAPIOfflineMgr**. Because **IMAPIOfflineMgr** inherits from [IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28v=VS.85%29.aspx), the client can query this interface (by using [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx)) to obtain a pointer to the interface pointer for **IMAPIOffline** for the offline object. The client can then get or set the current state of the object, or find out about the callback capabilities of the object (by calling **IMAPIOffline::GetCapabilities** ) and choose to set up callbacks by using **[IMAPIOfflineMgr](imapiofflinemgrimapioffline.md)**. 
  
A member in this interface is a placeholder reserved for the internal use of Microsoft Outlook 2013 and is subject to change. Other members in this interface must be used only as documented. 
  
## See also



[IMAPIOfflineMgr : IMAPIOffline](imapiofflinemgrimapioffline.md)


[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[MAPI Interfaces](mapi-interfaces.md)

