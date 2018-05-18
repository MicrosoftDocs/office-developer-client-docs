---
title: "IMAPISyncProgressCallbackProgress"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISyncProgressCallback.Progress
api_type:
- COM
ms.assetid: 6797cd1c-8a0b-4f42-ba56-6162d8e7b058
description: "Last modified: July 23, 2011"
---

# IMAPISyncProgressCallback::Progress

  
  
**Applies to**: Outlook 
  
Updates the status in the Send/Receive dialog. The store provider periodically calls this function.
  
```cpp
HRESULT Progress(
  const WCHAR *pwcszProgress, 
  ULONG ulIndex, 
  ULONG ulIndexMax
);
```

## Parameters

 **pwczsProgress**
  
> A pointer to a string that displays the current progress step. It can be NULL to update progress.
    
 **ulIndex**
  
> The current position in progress.
    
 **ulIndexMax**
  
> The index indicating complete progress.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## See also

#### Reference

[IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md)

