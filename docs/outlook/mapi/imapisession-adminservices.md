---
title: "IMAPISessionAdminServices"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISession.AdminServices
api_type:
- COM
ms.assetid: 487fab39-5c2c-4e1a-9f90-4da64f5e198b
description: "Last modified: March 09, 2015"
---

# IMAPISession::AdminServices

  
  
**Applies to**: Outlook 
  
Returns an [IMsgServiceAdmin](imsgserviceadminiunknown.md) pointer for making changes to message services. 
  
```cpp
HRESULT AdminServices(
  ULONG ulFlags,
  LPSERVICEADMIN FAR * lppServiceAdmin
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lppServiceAdmin_
  
> [out] A pointer to a pointer to a message service administration object.
    
## Return value

S_OK 
  
> A pointer to a message service administration object was successfully returned.
    
## Notes to callers

The **IMAPISession::AdminServices** method creates a message service administration object, an object that supports the **IMsgServiceAdmin** interface and returns a pointer. By using this pointer, you can call **IMsgServiceAdmin** methods to change any of the message services in the session profile. Be aware that these changes do not take effect until the next session; the current session is unaffected. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIStoreFunctions.cpp  <br/> |GetServerName  <br/> |MFCMAPI uses the **IMAPISession::AdminServices** method to access the profile to read the server name.  <br/> |
   
## See also



[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)
  
[IProfAdmin::AdminServices](iprofadmin-adminservices.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

