---
title: "IMAPISyncProgressCallbackError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISyncProgressCallback.Error
api_type:
- COM
ms.assetid: 4860992d-65d7-4cb0-a874-ceccb153dbac
---

# IMAPISyncProgressCallback::Error

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides details that are displayed in the Send/Receive dialog. If errors are encountered during synchronization, the store provider calls this function.
  
```cpp
HRESULT Error(
  HRESULT hResult,
  const WCHAR *pwcszErrorStr
);
```

## Parameters

 **hResult**
  
> The HRESULT of the error or warning.
    
 **pwcszErrorStr**
  
> A pointer to the string associated with the error to be displayed.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## See also



[IMAPISyncProgressCallback : IUnknown](imapisyncprogresscallbackiunknown.md)

