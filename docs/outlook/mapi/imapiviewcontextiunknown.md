---
title: "IMAPIViewContext  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewContext
api_type:
- COM
ms.assetid: d566ff39-92c1-4a14-85e5-1c406825f805
description: "Last modified: March 09, 2015"
---

# IMAPIViewContext : IUnknown

  
  
**Applies to**: Outlook 
  
Manages a form in a client application's form viewer. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |View context objects  <br/> |
|Implemented by:  <br/> |Form viewers  <br/> |
|Called by:  <br/> |Form objects  <br/> |
|Interface identifier:  <br/> |IID_IMAPIViewContext  <br/> |
|Pointer type:  <br/> |LPMAPIVIEWCONTEXT  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[SetAdviseSink](imapiviewcontext-setadvisesink.md) <br/> |Manages a form's registration to receive notifications about changes in the viewer.  <br/> |
|[ActivateNext](imapiviewcontext-activatenext.md) <br/> |Activates the next or previous message in the form viewer.  <br/> |
|[GetPrintSetup](imapiviewcontext-getprintsetup.md) <br/> |Retrieves current printing information.  <br/> |
|[GetSaveStream](imapiviewcontext-getsavestream.md) <br/> |Retrieves a stream to be used for saving the current message.  <br/> |
|[GetViewStatus](imapiviewcontext-getviewstatus.md) <br/> |Retrieves the current viewer status.  <br/> |
|[GetLastError](imapiviewcontext-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring in the view context object.  <br/> |
   
## See also

#### Concepts

[MAPI Interfaces](mapi-interfaces.md)

