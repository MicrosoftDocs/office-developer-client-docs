---
title: "IMAPISyncProgressCallback  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISyncProgressCallback
api_type:
- COM
ms.assetid: 146b5e36-8d73-4949-9fed-1074f707423d
description: "Last modified: March 09, 2015"
---

# IMAPISyncProgressCallback : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Passes the store provider as a field on the MAPISIB structure during a call to [IMAPISync : SynchronizeInBackground](imapisyncsynchronizeinbackground.md). The store provider uses this interface to provide feedback to Microsoft Outlook about the status of the synchronization.
  
|||
|:-----|:-----|
|Header file:  <br/> ||
|Exposed by:  <br/> |Outlook  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
|Called by:  <br/> |Store providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPISyncProgressCallback  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[Progress](imapisyncprogresscallback-progress.md) <br/> |The store provider periodically calls this function to update the status in the Send/Receive dialog.  <br/> |
|[Error](imapisyncprogresscallback-error.md) <br/> |If errors are encountered during synchronization, the store provider calls this function to provide details that are displayed in the Send/Receive dialog.  <br/> |
|[Done](imapisyncprogresscallback-done.md) <br/> |The store provider calls this function to inform Outlook that synchronization has completed.  <br/> |
   
## See also



[IMAPISync : IUnknown](imapisynciunknown.md)


[MAPI Interfaces](mapi-interfaces.md)

