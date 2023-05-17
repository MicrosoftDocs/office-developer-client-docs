---
title: "IMAPIViewAdviseSink  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIViewAdviseSink
api_type:
- COM
ms.assetid: 1231391d-803a-4b41-b252-4d986f99361a
description: "Receives notifications from forms for Outlook 2013 and Outlook 2016."
---

# IMAPIViewAdviseSink : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Receives notifications from forms. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |View advise sink objects  <br/> |
|Implemented by:  <br/> |Form viewers  <br/> |
|Called by:  <br/> |Form objects  <br/> |
|Interface identifier:  <br/> |IID_IMAPIViewAdviseSink  <br/> |
|Pointer type:  <br/> |LPMAPIVIEWADVISESINK  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[OnShutdown](imapiviewadvisesink-onshutdown.md) <br/> |Notifies the form viewer that a form is being closed. |
|[OnNewMessage](imapiviewadvisesink-onnewmessage.md) <br/> |Notifies the form viewer that either a new or an existing message has been loaded in a form. |
|[OnPrint](imapiviewadvisesink-onprint.md) <br/> |Notifies the form viewer of the printing status of a form. |
|[OnSubmitted](imapiviewadvisesink-onsubmitted.md) <br/> |Notifies the form viewer that the current message has been submitted to MAPI spooler. |
|[OnSaved](imapiviewadvisesink-onsaved.md) <br/> |Notifies the form viewer that the current message in a form has been saved. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

