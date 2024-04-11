---
title: "IMAPIForm  IUnknown"
description: "IMAPIFormIUnknown enables form viewers to work with form view contexts and form notification, to perform form verbs, and to shut down forms."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIForm
api_type:
- COM
ms.assetid: e9059739-51b4-4574-bd0f-709eb5144ae7
---

# IMAPIForm : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Enables form viewers to work with form view contexts and form notification, to perform form verbs, and to shut down forms.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Form objects  <br/> |
|Implemented by:  <br/> |Form servers  <br/> |
|Called by:  <br/> |Form viewers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIForm  <br/> |
|Pointer type:  <br/> |LPMAPIFORM  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[SetViewContext](imapiform-setviewcontext.md) <br/> |Establishes a view context for the form. |
|[GetViewContext](imapiform-getviewcontext.md) <br/> |Returns the current view context for the form. |
|[ShutdownForm](imapiform-shutdownform.md) <br/> |Closes the form. |
|[DoVerb](imapiform-doverb.md) <br/> |Requests that the form perform whatever tasks it associates with a specific verb. |
|[Advise](imapiform-advise.md) <br/> |Registers a form viewer for notifications about events that affect the form. |
|[Unadvise](imapiform-unadvise.md) <br/> |Cancels a registration for notifications with a form viewer previously established by calling **Advise**. |
|[GetLastError](imapiform-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring to the form object. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

