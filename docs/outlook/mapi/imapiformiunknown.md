---
title: "IMAPIForm  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIForm
api_type:
- COM
ms.assetid: e9059739-51b4-4574-bd0f-709eb5144ae7
description: "Last modified: March 09, 2015"
---

# IMAPIForm : IUnknown

  
  
**Applies to**: Outlook 
  
Enables form viewers to work with form view contexts and form notification, to perform form verbs, and to shut down forms.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Form objects  <br/> |
|Implemented by:  <br/> |Form servers  <br/> |
|Called by:  <br/> |Form viewers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIForm  <br/> |
|Pointer type:  <br/> |LPMAPIFORM  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[SetViewContext](imapiform-setviewcontext.md) <br/> |Establishes a view context for the form.  <br/> |
|[GetViewContext](imapiform-getviewcontext.md) <br/> |Returns the current view context for the form.  <br/> |
|[ShutdownForm](imapiform-shutdownform.md) <br/> |Closes the form.  <br/> |
|[DoVerb](imapiform-doverb.md) <br/> |Requests that the form perform whatever tasks it associates with a specific verb.  <br/> |
|[Advise](imapiform-advise.md) <br/> |Registers a form viewer for notifications about events that affect the form.  <br/> |
|[Unadvise](imapiform-unadvise.md) <br/> |Cancels a registration for notifications with a form viewer previously established by calling **Advise**.  <br/> |
|[GetLastError](imapiform-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring to the form object.  <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

