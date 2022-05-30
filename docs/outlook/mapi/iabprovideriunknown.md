---
title: "IABProvider  IUnknown"
description: Provides a method to log on to an address book provider object and a method to invalidate an address book provider object.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IABProvider
api_type:
- COM
ms.assetid: 3f98d982-156d-43d7-8b0b-94d8c24debef
---

# IABProvider : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides a method to log on to an address book provider object and a method to invalidate an address book provider object.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Address book provider objects  <br/> |
|Implemented by:  <br/> |Address book providers  <br/> |
|Called by:  <br/> |MAPI  <br/> |
|Interface identifier:  <br/> |IID_IABProvider  <br/> |
|Pointer type:  <br/> |LPABPROVIDER  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[Logon](iabprovider-logon.md) <br/> |Establishes a connection to an active session. |
|[Shutdown](iabprovider-shutdown.md) <br/> |Cancels a connection to an active session. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

