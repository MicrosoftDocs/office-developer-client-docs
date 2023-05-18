---
title: "IMAPISyncProgressCallbackDone"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISyncProgressCallback.Done
api_type:
- COM
ms.assetid: aaa8eb56-f22f-4c5a-a224-807ff001e0ca
---

# IMAPISyncProgressCallback::Done

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 Informs Microsoft Outlook that synchronization is complete. 
  
```cpp
HRESULT Done(
  HANDLE hThreadDoneEvent, 
  HRESULT hResult
);
```

## Parameters

 **hThreadDoneEvent**
  
> An event that is passed back to allow Microsoft Outlook to close the handle. It can be NULL.
    
 **hResult**
  
> An HRESULT indicating final status of the progress.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## See also



[IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md)

