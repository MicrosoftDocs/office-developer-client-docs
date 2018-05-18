---
title: "IMAPIFormAdviseSink  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormAdviseSink
api_type:
- COM
ms.assetid: 180022af-4c1c-408c-a3fe-ed075cef79ab
description: "Last modified: March 09, 2015"
---

# IMAPIFormAdviseSink : IUnknown

  
  
**Applies to**: Outlook 
  
Enables form servers to receive notifications from form viewers. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Form advise sink objects  <br/> |
|Implemented by:  <br/> |Form servers  <br/> |
|Called by:  <br/> |Form viewers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIFormAdviseSink  <br/> |
|Pointer type:  <br/> |LPMAPIFORMADVISESINK  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[OnChange](imapiformadvisesink-onchange.md) <br/> |Indicates that a change has occurred in the status of the form viewer.  <br/> |
|[OnActivateNext](imapiformadvisesink-onactivatenext.md) <br/> |Indicates whether the form can handle the message class of the next message to display.  <br/> |
   
## Remarks

Form servers use a form advise sink object to implement **IMAPIFormAdviseSink** instead of including it with their form object. Therefore, form viewers should expect a failed call to a form's [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx) method to obtain a pointer to this interface. 
  
Form servers call a viewer's [IMAPIViewContext::SetAdviseSink](imapiviewcontext-setadvisesink.md) method to register for notifications. A pointer to their **IMAPIFormAdviseSink** implementation is included as a parameter. 
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

