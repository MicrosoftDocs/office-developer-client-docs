---
title: "IXPProvider  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IXPProvider
api_type:
- COM
ms.assetid: d5507785-c924-4981-ae80-19709ceb054d
description: "Last modified: March 09, 2015"
---

# IXPProvider : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Initializes a transport provider object and shuts down the object when it is no longer needed.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Transport provider objects  <br/> |
|Implemented by:  <br/> |Transport providers  <br/> |
|Called by:  <br/> |The MAPI spooler  <br/> |
|Interface identifier:  <br/> |IID_IXPProvider  <br/> |
|Pointer type:  <br/> |LPXPROVIDER  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[Shutdown](ixpprovider-shutdown.md) <br/> |Closes down a transport provider in an orderly fashion. |
|[TransportLogon](ixpprovider-transportlogon.md) <br/> |Establishes a session in which a client application logs on to a transport provider. |
   

