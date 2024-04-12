---
title: "IMAPISync  IUnknown"
description: "IMAPISyncIUnknown provides a mechanism for synchronizing email instead of using the Transport API. This interface is exposed on a store object."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISync
api_type:
- COM
ms.assetid: c14d1012-f3d4-47eb-8a90-3160331f94e8
---

# IMAPISync : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides a mechanism for synchronizing email instead of using the Transport API. This interface is exposed on a store object. By using this interface and [IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md), a transport provider can provide better progress and error messages than those that appear in the Send/Receive dialog in Microsoft Outlook.
  
The outbox is still in the default store. Outlook will continue to use the Transport APIs to send mail because the outgoing message cannot be in the external store.
  
|Property|Value|
|:-----|:-----|
|Exposed by:  <br/> |Store and transport providers  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
|Called by:  <br/> |Store and Transport providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPISync  <br/> |
   
## Vtable order

|Member|Description|
|:-----|:-----|
|[SynchronizeInBackground](imapisyncsynchronizeinbackground.md) <br/> |Implemented by message store providers. This method is called by Outlook 2010 and Outlook 2013 to start synchronization. |
   
## See also



[IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md)


[MAPI Interfaces](mapi-interfaces.md)

