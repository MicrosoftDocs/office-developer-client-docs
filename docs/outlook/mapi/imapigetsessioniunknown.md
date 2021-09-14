---
title: "IMAPIGetSession  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIGetSession
api_type:
- COM
ms.assetid: d1b662e2-1516-46b2-ba94-4092d79b5a39
description: "Last modified: March 09, 2015"
---

# IMAPIGetSession : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to the current MAPI session associated with the support object. MAPI Providers can query their MAPI Support Object for this interface. For more information on support objects, see [Support Object Overview](support-object-overview.md).
  
|||
|:-----|:-----|
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |MAPI Providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIGetSession  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetMAPISession](imapigetsession-getmapisession.md) <br/> |Called to obtain a pointer to the current MAPI session.  <br/> |
   
## See also



[GetMAPISession](imapigetsession-getmapisession.md)
  
[IMAPISupport](imapisupportiunknown.md)


[MAPI Interfaces](mapi-interfaces.md)
  
[Support Object Overview](support-object-overview.md)

