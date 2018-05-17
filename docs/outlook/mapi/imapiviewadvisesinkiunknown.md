---
title: "IMAPIViewAdviseSink  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewAdviseSink
api_type:
- COM
ms.assetid: 1231391d-803a-4b41-b252-4d986f99361a
description: "Last modified: March 09, 2015"
---

# IMAPIViewAdviseSink : IUnknown

  
  
**Applies to**: Outlook 
  
Receives notifications from forms. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |View advise sink objects  <br/> |
|Implemented by:  <br/> |Form viewers  <br/> |
|Called by:  <br/> |Form objects  <br/> |
|Interface identifier:  <br/> |IID_IMAPIViewAdviseSink  <br/> |
|Pointer type:  <br/> |LPMAPIVIEWADVISESINK  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[OnShutdown](imapiviewadvisesink-onshutdown.md) <br/> |Notifies the form viewer that a form is being closed.  <br/> |
|[OnNewMessage](imapiviewadvisesink-onnewmessage.md) <br/> |Notifies the form viewer that either a new or an existing message has been loaded in a form.  <br/> |
|[OnPrint](imapiviewadvisesink-onprint.md) <br/> |Notifies the form viewer of the printing status of a form.  <br/> |
|[OnSubmitted](imapiviewadvisesink-onsubmitted.md) <br/> |Notifies the form viewer that the current message has been submitted to MAPI spooler.  <br/> |
|[OnSaved](imapiviewadvisesink-onsaved.md) <br/> |Notifies the form viewer that the current message in a form has been saved.  <br/> |
   
## See also

#### Concepts

[MAPI Interfaces](mapi-interfaces.md)

