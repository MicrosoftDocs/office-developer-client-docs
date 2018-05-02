---
title: "IXPProvider  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPProvider
api_type:
- COM
ms.assetid: d5507785-c924-4981-ae80-19709ceb054d
description: "Last modified: March 09, 2015"
---

# IXPProvider : IUnknown

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Initializes a transport provider object and shuts down the object when it is no longer needed.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Transport provider objects  <br/> |
|Implemented by:  <br/> |Transport providers  <br/> |
|Called by:  <br/> |The MAPI spooler  <br/> |
|Interface identifier:  <br/> |IID_IXPProvider  <br/> |
|Pointer type:  <br/> |LPXPROVIDER  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[Shutdown](ixpprovider-shutdown.md) <br/> |Closes down a transport provider in an orderly fashion.  <br/> |
|[TransportLogon](ixpprovider-transportlogon.md) <br/> |Establishes a session in which a client application logs on to a transport provider.  <br/> |
   

