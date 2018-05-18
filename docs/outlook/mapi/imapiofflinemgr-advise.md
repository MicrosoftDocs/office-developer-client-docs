---
title: "IMAPIOfflineMgrAdvise"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOfflineMgr.Advise
api_type:
- COM
ms.assetid: 784b6218-548d-817a-caaa-cf9be6bc3d2f
description: "Last modified: July 23, 2011"
---

# IMAPIOfflineMgr::Advise

  
  
**Applies to**: Outlook 
  
Registers a client to receive callbacks on an offline object.
  
```cpp
HRESULT COfflineObj::Advise( 
      ULONG ulFlags, 
      MAPIOFFLINE_ADVISEINFO* pAdviseInfo, 
      ULONG* pulAdviseToken 
);
```

## Parameters

 _ulFlags_
  
>  [in] Flags that modify behavior. Only the value MAPIOFFLINE_ADVISE_DEFAULT is supported. 
    
 _pAdviseInfo_
  
> [in] Information about the type of callback, when to receive a callback, a callback interface for the caller, and other details. It also contains a client token that Outlook uses in sending subsequent notification callbacks to the client caller.
    
 _pulAdviseToken_
  
> [out] An advise token returned to the client caller for subsequently canceling callback for the object.
    
## Return value

S_OK
  
> The call was successful.
    
E_INVALIDARG
  
> An invalid parameter has been specified.
    
E_NOINTERFACE
  
> The callback interface specified in  *pAdviseInfo*  is not valid. 
    
## Remarks

Upon opening an offline object using **[HrOpenOfflineObj](hropenofflineobj.md)**, a client obtains an offline object that supports **IMAPIOfflineMgr**. The client can check for the kinds of callbacks supported by the object by using **[IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)**. The client can determine the type and other details about the callback it wants, and then call **IMAPIOfflineMgr::Advise** to register to receive such callbacks about the object. 
  
## See also

#### Reference

[IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)
  
[IMAPIOfflineMgr::Unadvise](imapiofflinemgr-unadvise.md)
#### Concepts

[MAPI Constants](mapi-constants.md)
  
[HrOpenOfflineObj](hropenofflineobj.md)

