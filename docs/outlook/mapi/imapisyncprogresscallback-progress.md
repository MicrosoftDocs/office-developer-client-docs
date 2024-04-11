---
title: "IMAPISyncProgressCallbackProgress"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISyncProgressCallback.Progress
api_type:
- COM
ms.assetid: 6797cd1c-8a0b-4f42-ba56-6162d8e7b058
---

# IMAPISyncProgressCallback::Progress

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
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



[IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md)

