---
title: "IMAPIFormFactory  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormFactory
api_type:
- COM
ms.assetid: 637be364-c393-430a-84b3-2c96aa553c22
description: "Last modified: March 09, 2015"
---

# IMAPIFormFactory : IUnknown

  
  
**Applies to**: Outlook 
  
Supports the use of configurable run-time forms in distributed computing environments. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Form factory objects  <br/> |
|Implemented by:  <br/> |Form servers  <br/> |
|Called by:  <br/> |Form viewers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIFormFactory  <br/> |
|Pointer type:  <br/> |LPMAPIFORMFACTORY  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[CreateClassFactory](imapiformfactory-createclassfactory.md) <br/> |Returns a class factory object for the form.  <br/> |
|[GetLastError](imapiformfactory-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring to the form factory object.  <br/> |
|[LockServer](imapiformfactory-lockserver.md) <br/> |Keeps an open form server in memory.  <br/> |
   
## Remarks

The **IMAPIFormFactory** interface is based on the [IClassFactory](http://msdn.microsoft.com/en-us/library/ms694364%28VS.85%29.aspx) interface, and objects that implement **IMAPIFormFactory** should also inherit from **IClassFactory**.
  
 **IMAPIFormFactory** is the interface that form viewers use to create new form objects when a form server supports more than one message class (that is, more than one type of form object). 
  
## See also

#### Concepts

[MAPI Interfaces](mapi-interfaces.md)

