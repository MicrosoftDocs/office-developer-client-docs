---
title: "IMAPIFormContainer  IUnknown"
description: "IMAPIFormContainerIUnknown manages forms in form libraries. This interface is used to create application-specific form libraries."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormContainer
api_type:
- COM
ms.assetid: 437c8a75-1121-4919-8bd4-d57c0d6f4b9a
---

# IMAPIFormContainer : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Manages forms in form libraries. This interface is used to create application-specific form libraries. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Form container objects  <br/> |
|Implemented by:  <br/> |Form library providers  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIFormContainer  <br/> |
|Pointer type:  <br/> |LPMAPIFORMCONTAINER  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[InstallForm](imapiformcontainer-installform.md) <br/> |Installs a form into a form container. |
|[RemoveForm](imapiformcontainer-removeform.md) <br/> |Removes a particular form from a form container. |
|[ResolveMessageClass](imapiformcontainer-resolvemessageclass.md) <br/> |Resolves a message class to its form in a form container and returns a form information object for that form. |
|[ResolveMultipleMessageClasses](imapiformcontainer-resolvemultiplemessageclasses.md) <br/> |Resolves a group of message classes to their forms in a form container and returns an array of form information objects for those forms. |
|[CalcFormPropSet](imapiformcontainer-calcformpropset.md) <br/> |Returns an array of the properties used by all forms installed in a form container. |
|[GetDisplay](imapiformcontainer-getdisplay.md) <br/> |Returns the display name of a form container. |
|[GetLastError](imapiformcontainer-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure containing information about the previous error occurring to the form container object. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

