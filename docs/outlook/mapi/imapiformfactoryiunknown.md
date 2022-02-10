---
title: "IMAPIFormFactory  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormFactory
api_type:
- COM
ms.assetid: 637be364-c393-430a-84b3-2c96aa553c22
description: "Last modified: March 09, 2015"
---

# IMAPIFormFactory : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Supports the use of configurable run-time forms in distributed computing environments. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Form factory objects  <br/> |
|Implemented by:  <br/> |Form servers  <br/> |
|Called by:  <br/> |Form viewers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIFormFactory  <br/> |
|Pointer type:  <br/> |LPMAPIFORMFACTORY  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[CreateClassFactory](imapiformfactory-createclassfactory.md) <br/> |Returns a class factory object for the form. |
|[GetLastError](imapiformfactory-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring to the form factory object. |
|[LockServer](imapiformfactory-lockserver.md) <br/> |Keeps an open form server in memory. |
   
## Remarks

The **IMAPIFormFactory** interface is based on the [IClassFactory](https://msdn.microsoft.com/library/ms694364%28VS.85%29.aspx) interface, and objects that implement **IMAPIFormFactory** should also inherit from **IClassFactory**.
  
 **IMAPIFormFactory** is the interface that form viewers use to create new form objects when a form server supports more than one message class (that is, more than one type of form object). 
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

