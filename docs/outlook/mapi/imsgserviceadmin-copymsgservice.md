---
title: "IMsgServiceAdminCopyMsgService"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin.CopyMsgService
api_type:
- COM
ms.assetid: a13c6757-358f-421a-9a76-de7483501613
---

# IMsgServiceAdmin::CopyMsgService

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies a message service into a profile. 
  
```cpp
HRESULT CopyMsgService(
  LPMAPIUID lpUID,
  LPSTR lpszDisplayName,
  LPCIID lpInterfaceToCopy,
  LPCIID lpInterfaceDst,
  LPVOID lpObjectDst,
  ULONG_PTR ulUIParam,
  ULONG ulFlags
);
```

## Parameters

 _lpUID_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier of the message service to copy. 
    
 _lpszDisplayName_
  
> [in] This parameter has been deprecated. 
    
 _lpInterfaceToCopy_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the profile section of the message service to copy. Passing NULL results in the standard profile section interface, [IProfSect](iprofsectimapiprop.md), being used.
    
 _lpInterfaceDst_
  
> [in] A pointer to the IID that represents the interface to be used to access the object pointed to by the  _lpObjectDst_ parameter. Passing NULL results in the session interface, [IMAPISession](imapisessioniunknown.md), being used. The  _lpInterfaceDst_ parameter can also be set to IID_IMsgServiceAdmin. 
    
 _lpObjectDst_
  
> [in] A pointer to a pointer to a session or message service administration object. The type of object should correspond to the interface identifier passed in  _lpInterfaceDst_. Valid object pointers are LPMAPISESSION and LPSERVICEADMIN.
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows this method displays.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the message service is copied. The following flags can be set:
    
SERVICE_UI_ALWAYS 
  
> Requests that the message service always display a configuration property sheet.
    
## Return value

S_OK 
  
> The message service was successfully copied.
    
MAPI_E_NO_ACCESS 
  
> The message service is already in the profile and does not allow multiple instances of itself.
    
MAPI_E_NOT_FOUND 
  
> The **MAPIUID** pointed to by  _lpUID_ does not refer to an existing message service. 
    
## Remarks

The **IMsgServiceAdmin::CopyMsgService** method copies a message service into a profile, either the active profile or another profile. The profile that contains the message service to be copied and the destination do not have to be the same profile, but they can be. 
  
The message service's entry point function is not called for a copy operation. The copied message service has the same configuration settings as its original. To change these settings, a client should call the [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md) method. 
  
## See also



[IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md)
  
[MAPIUID](mapiuid.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)

