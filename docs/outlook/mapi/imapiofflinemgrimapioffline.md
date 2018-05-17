---
title: "IMAPIOfflineMgr  IMAPIOffline"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOfflineMgr
api_type:
- COM
ms.assetid: 3e430308-190c-c9bb-fffc-c26ffecb73a5
description: "Last modified: March 09, 2015"
---

# IMAPIOfflineMgr : IMAPIOffline

  
  
**Applies to**: Outlook 
  
Supports registering for notification callbacks about connection state changes of a user account.
  
|||
|:-----|:-----|
|Exported by:  <br/> |msmapi32.dll  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
|Called by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IMAPIOfflineMgr  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[Advise](imapiofflinemgr-advise.md) <br/> |Registers for notification callbacks about connection changes.  <br/> |
|[Unadvise](imapiofflinemgr-unadvise.md) <br/> |Removes a given registration for notification callbacks.  <br/> |
| *Placeholder member*  <br/> | *This member is a placeholder and is not supported.*  <br/> |
| *Placeholder member*  <br/> | *This member is a placeholder and is not supported.*  <br/> |
| *Placeholder member*  <br/> | *This member is a placeholder and is not supported.*  <br/> |
| *Placeholder member*  <br/> | *This member is a placeholder and is not supported.*  <br/> |
| *Placeholder member*  <br/> | *This member is a placeholder and is not supported.*  <br/> |
| *Placeholder member*  <br/> | *This member is a placeholder and is not supported.*  <br/> |
| *Placeholder member*  <br/> | *This member is a placeholder and is not supported.*  <br/> |
   
## Remarks

Upon opening an offline object for a user account profile using **[HrOpenOfflineObj](hropenofflineobj.md)**, a client obtains an offline object that supports **IMAPIOfflineMgr**. 
  
Because this interface inherits from **[IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28v=VS.85%29.aspx)**, the client can query this interface (by using **[IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx)** ) to obtain an object that supports **[IMAPIOffline](imapiofflineiunknown.md)**. The client can then find out about the callback capabilities of the offline object (by calling **[IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)** ), and choose to set up callbacks (by using **IMAPIOfflineMgr::Advise** ). 
  
Most of the members in this interface are placeholders reserved for the internal use of Outlook and are subject to change. Callers of this interface must use non-placeholder members only as documented.
  
## See also

#### Reference

[IMAPIOffline : IUnknown](imapiofflineiunknown.md)
#### Concepts

[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[HrOpenOfflineObj](hropenofflineobj.md)
  
[MAPI Interfaces](mapi-interfaces.md)

