---
title: "HrOpenOfflineObj"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- HrOpenOfflineObj
api_type:
- HeaderDef
ms.assetid: cee1a940-fe01-d364-5d7c-c9e9dfeb8979
description: "Last modified: March 09, 2015"
---

# HrOpenOfflineObj

  
  
**Applies to**: Outlook 
  
Opens an offline object based on a given profile.
  
## Quick Info

|||
|:-----|:-----|
|Exported by:  <br/> |msmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
   
```
typedef HRESULT (STDMETHODCALLTYPE HROPENOFFLINEOBJ)( 
      ULONG ulReserved, 
      LPCWSTR pwszProfileNameIn, 
      const GUID* pGUID, 
      const GUID* pReserved, 
      IMAPIOfflineMgr** ppOfflineObj); 

```

## Parameters

 _ulReserved_
  
> [in] This parameter is not used. It must be 0.
    
 _pwszProfileNameIn_
  
> [in] The name of the profile that the offline object is for. It must be expressed in Unicode. 
    
 _pGUID_
  
> [in] Pointer to a GUID which can be used to uniquely identify this object from other offline objects. It must be **GUID_GlobalState**.
    
 _pReserved_
  
> [in] This parameter is not used. It must be **null**.
    
 _ppOfflineObj_
  
> [out] A pointer to the requested offline object. The caller can use this pointer to access the [IMAPIOfflineMgr : IMAPIOffline](imapiofflinemgrimapioffline.md) interface to find the callbacks that this object supports and to set up callbacks for it. 
    
## Return Values

S_OK 
  
- The function call is successful.
    
MAPI_E_NOT_FOUND
  
- The function call failed.
    
## Remarks

This is the first call that a client makes when the client wants to be notified of any connection state changes for a given profile. Upon calling **HrOpenOfflineObj**, the client obtains an offline object that supports **IMAPIOfflineMgr**. The client can check for the kinds of callbacks supported by the object (by using [IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)), and then set up callbacks for it (by using [IMAPIOfflineMgr::Advise](imapiofflinemgr-advise.md)).
  
When using [GetProcAddress](http://msdn.microsoft.com/en-us/library/ms683212.aspx) to look for the address of this function in msmapi32.dll, specify **HrOpenOfflineObj@20** as the procedure name. 
  
 **HrOpenOfflineObj** only works for clients that are MAPI providers, COM Add-Ins, and Exchange Client Extensions running inside the Outlook process. Otherwise, **HrOpenOfflineObj** returns **MAPI_E_NOT_FOUND**. 
  
## See also

#### Reference

[IMAPIOffline : IUnknown](imapiofflineiunknown.md)
  
[IMAPIOfflineMgr : IMAPIOffline](imapiofflinemgrimapioffline.md)
#### Concepts

[About the Offline State API](about-the-offline-state-api.md)
  
[MAPI Constants](mapi-constants.md)

