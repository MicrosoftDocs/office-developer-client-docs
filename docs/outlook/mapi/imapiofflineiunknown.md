---
title: "IMAPIOffline  IUnknown"
description: "Describes the properties, vtable order, and remarks for IMAPIOfflineIUnknown, which provides information for an offline object."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIOffline
api_type:
- COM
ms.assetid: 211281ff-3c22-1b51-4b72-ca1e313c7202
---

# IMAPIOffline : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides information for an offline object.
  
|Property |Value |
|:-----|:-----|
|Provided by:  <br/> |Query on [IMAPIOfflineMgr](imapiofflinemgrimapioffline.md) <br/> |
|Called by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IMAPIOffline  <br/> |
   
## Vtable order

|Member|Value |
|:-----|:-----|
|**[SetCurrentState](imapioffline-setcurrentstate.md)** <br/> |Sets the current state of an offline object to online or offline. |
|**[GetCapabilities](imapioffline-getcapabilities.md)** <br/> |Gets the conditions for which callbacks are supported by an offline object. |
|**[GetCurrentState](imapioffline-getcurrentstate.md)** <br/> |Gets the current online or offline state of an offline object. |
| *Placeholder member*  <br/> |This member is a placeholder and is not supported. |
   
## Remarks

A client uses **[HrOpenOfflineObj](hropenofflineobj.md)** to open and obtain an offline object that supports **IMAPIOfflineMgr**. Because **IMAPIOfflineMgr** inherits from [IUnknown](https://msdn.microsoft.com/library/ms680509%28v=VS.85%29.aspx), the client can query this interface (by using [IUnknown::QueryInterface](https://msdn.microsoft.com/library/ms682521%28v=VS.85%29.aspx)) to obtain a pointer to the interface pointer for **IMAPIOffline** for the offline object. The client can then get or set the current state of the object, or find out about the callback capabilities of the object (by calling **IMAPIOffline::GetCapabilities** ) and choose to set up callbacks by using **[IMAPIOfflineMgr](imapiofflinemgrimapioffline.md)**. 
  
A member in this interface is a placeholder reserved for the internal use of Microsoft Outlook 2013 and is subject to change. Other members in this interface must be used only as documented. 
  
## See also



[IMAPIOfflineMgr : IMAPIOffline](imapiofflinemgrimapioffline.md)


[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[MAPI Interfaces](mapi-interfaces.md)

