---
title: "MAPISIB"
description: "Describes the syntax and members of MAPISIB, which is a structure used with IMAPISync SynchronizeInBackground."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 16452798-7a95-43da-b95e-908debcea050
---

# MAPISIB

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This structure is used with [IMAPISync::SynchronizeInBackground](imapisyncsynchronizeinbackground.md).
  
```cpp
typedef struct _MAPISIB
{
ULONG           ulSize;                
ULONG           ulFlags;
LPMAPISESSION   psesSync;
LPUNKNOWN       punkCallBack;
HANDLE          *phSyncDoneEvent;    
} MAPISIB, *PMAPISIB
```

## Members

 **ulSize**
  
> The size of the structure.
    
 **ulFlags**
  
> A flag that indicates the type of sync. It must be one of the following values:
    
|Flag |Value |Description |
|:-----|:-----|:-----|
|SYNC_OUTGOING_MAIL  <br/> |0x00000200  <br/> |Send the message to the server (not currently in use). |
|SYNC_UPLOAD_HIERARCHY  <br/> |0x00000001  <br/> |Push hierarchy changes to the server. |
|SYNC_DOWNLOAD_HIERARCHY  <br/> |0x00000002  <br/> |Pull hierarchy changes from server. |
|SYNC_UPLOAD_CONTENTS  <br/> |0x00000040  <br/> |Push message changes to server. |
|SYNC_DOWNLOAD_CONTENTS  <br/> |0x00000080  <br/> |Pull message changes from server. |
|SYNC_ON_DEMAND  <br/> |0x20000000  <br/> |The sync was initiated by the user and should be a higher priority. |
|SYNC_GLOBAL_HEADERS  <br/> |0x02000000  <br/> |Should only sync headers and not full bodies. |
   
 **psesSync**
  
> [IN] A pointer to the MAPI session.
    
 **punkCallBack**
  
> [IN] A pointer to the interface on which to provide progress. It can be used to query the interface for [IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md).
    
 **\*phSyncDoneEvent**
  
> [OUT] The event that will occur when the thread that was just created is complete. The pointer must be valid because it will contain the event.
    
## See also



[IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md)
  
[IMAPISync : IUnknown](imapisynciunknown.md)

