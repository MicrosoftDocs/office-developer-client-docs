---
title: "IMAPIGetSession  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIGetSession
api_type:
- COM
ms.assetid: d1b662e2-1516-46b2-ba94-4092d79b5a39
description: "Last modified: March 09, 2015"
---

# IMAPIGetSession : IUnknown

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Provides access to the current MAPI session associated with the support object. MAPI Providers can query their MAPI Support Object for this interface. For more information on support objects, see [Support Object Overview](support-object-overview.md).
  
|||
|:-----|:-----|
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |MAPI Providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIGetSession  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[GetMAPISession](imapigetsession-getmapisession.md) <br/> |Called to obtain a pointer to the current MAPI session.  <br/> |
   
## See also

#### Reference

[GetMAPISession](imapigetsession-getmapisession.md)
  
[IMAPISupport](imapisupportiunknown.md)
#### Concepts

[MAPI Interfaces](mapi-interfaces.md)
  
[Support Object Overview](support-object-overview.md)

