---
title: "IMAPIAdviseSink  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIAdviseSink
api_type:
- COM
ms.assetid: f598fc57-75d3-473b-8eb0-9d8a3b92e9f2
description: "Last modified: March 09, 2015"
---

# IMAPIAdviseSink : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Implements an advise sink object for handling notification. A pointer to an advise sink object is passed in a call to a service provider's **Advise** method, the mechanism used to register for notification. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Advise sink objects  <br/> |
|Implemented by:  <br/> |Client applications and MAPI  <br/> |
|Called by:  <br/> |Service providers and MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMAPIAdviseSink  <br/> |
|Pointer type:  <br/> |LPMAPIADVISESINK  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[OnNotify](imapiadvisesink-onnotify.md) <br/> |Responds to a notification by performing one or more tasks. The tasks performed depend on the type of event and the object that generates the notification. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

