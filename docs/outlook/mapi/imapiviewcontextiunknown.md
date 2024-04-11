---
title: "IMAPIViewContext  IUnknown"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIViewContext
api_type:
- COM
ms.assetid: d566ff39-92c1-4a14-85e5-1c406825f805
description: "Manages a form in a client application's form viewer for Outlook 2013 and Outlook 2016."
---

# IMAPIViewContext : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Manages a form in a client application's form viewer. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |View context objects  <br/> |
|Implemented by:  <br/> |Form viewers  <br/> |
|Called by:  <br/> |Form objects  <br/> |
|Interface identifier:  <br/> |IID_IMAPIViewContext  <br/> |
|Pointer type:  <br/> |LPMAPIVIEWCONTEXT  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[SetAdviseSink](imapiviewcontext-setadvisesink.md) <br/> |Manages a form's registration to receive notifications about changes in the viewer. |
|[ActivateNext](imapiviewcontext-activatenext.md) <br/> |Activates the next or previous message in the form viewer. |
|[GetPrintSetup](imapiviewcontext-getprintsetup.md) <br/> |Retrieves current printing information. |
|[GetSaveStream](imapiviewcontext-getsavestream.md) <br/> |Retrieves a stream to be used for saving the current message. |
|[GetViewStatus](imapiviewcontext-getviewstatus.md) <br/> |Retrieves the current viewer status. |
|[GetLastError](imapiviewcontext-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring in the view context object. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

