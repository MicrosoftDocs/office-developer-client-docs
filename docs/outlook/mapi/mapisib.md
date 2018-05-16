---
title: "MAPISIB"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 16452798-7a95-43da-b95e-908debcea050
description: "Last modified: March 09, 2015"
---

# MAPISIB

  
  
**Applies to**: Outlook 
  
This structure is used with [IMAPISync::SynchronizeInBackground](imapisyncsynchronizeinbackground.md).
  
```
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
    
||||
|:-----|:-----|:-----|
|SYNC_OUTGOING_MAIL  <br/> |0x00000200  <br/> |Send the message to the server (not currently in use).  <br/> |
|SYNC_UPLOAD_HIERARCHY  <br/> |0x00000001  <br/> |Push hierarchy changes to the server.  <br/> |
|SYNC_DOWNLOAD_HIERARCHY  <br/> |0x00000002  <br/> |Pull hierarchy changes from server.  <br/> |
|SYNC_UPLOAD_CONTENTS  <br/> |0x00000040  <br/> |Push message changes to server.  <br/> |
|SYNC_DOWNLOAD_CONTENTS  <br/> |0x00000080  <br/> |Pull message changes from server.  <br/> |
|SYNC_ON_DEMAND  <br/> |0x20000000  <br/> |The sync was initiated by the user and should be a higher priority.  <br/> |
|SYNC_GLOBAL_HEADERS  <br/> |0x02000000  <br/> |Should only sync headers and not full bodies.  <br/> |
   
 **psesSync**
  
> [IN] A pointer to the MAPI session.
    
 **punkCallBack**
  
> [IN] A pointer to the interface on which to provide progress. It can be used to query the interface for [IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md).
    
 **\*phSyncDoneEvent**
  
> [OUT] The event that will occur when the thread that was just created is complete. The pointer must be valid because it will contain the event.
    
## See also

#### Reference

[IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md)
  
[IMAPISync : IUnknown](imapisynciunknown.md)

