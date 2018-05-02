---
title: "IMAPIOfflineMgrUnadvise"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOfflineMgr.Unadvise
api_type:
- COM
ms.assetid: 250b9137-facb-81a2-41b1-96a57366c04e
description: "Last modified: July 23, 2011"
---

# IMAPIOfflineMgr::Unadvise

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Cancels callbacks for an offline object.
  
```
HRESULT COfflineObj::Unadvise( 
      ULONG ulFlags, 
      ULONG ulAdviseToken 
);
```

## Parameters

 _ulFlags_
  
> [in] Flags for canceling callback. Only the value MAPIOFFLINE_UNADVISE_DEFAULT is supported.
    
 _ulAdviseToken_
  
> [in] An advise token that identifies the callback registration that is to be canceled. 
    
## Return value

S_OK
  
> The call was successful. This call must return S_OK.
    
## Remarks

Removes the registration for the callback that was associated with  *ulAdviseToken*  returned from a prior call to **[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)**. Causes the **IMAPIOfflineMgr** object to release its reference on the **[IMAPIOfflineNotify](imapiofflinenotifyiunknown.md)** object associated with  *ulAdviseToken*  . 
  
## See also

#### Reference

[IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)
#### Concepts

[MAPI Constants](mapi-constants.md)

