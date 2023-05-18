---
title: "IMAPIStatusChangePassword"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIStatus.ChangePassword
api_type:
- COM
ms.assetid: 0cd1026a-342d-4d05-91ed-d3decced5bf3
---

# IMAPIStatus::ChangePassword

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Modifies a service provider's password without displaying a user interface. This method is optionally supported in status objects that service providers implement.
  
```cpp
HRESULT ChangePassword(
  LPSTR lpOldPass,
  LPSTR lpNewPass,
  ULONG ulFlags
);
```

## Parameters

 _lpOldPass_
  
> [in] A pointer to the old password.
    
 _lpNewPass_
  
> [in] A pointer to the new password.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the format of the passwords. The following flag can be set:
    
MAPI_UNICODE 
  
> The passwords are in Unicode format. If the MAPI_UNICODE flag is not set, the passwords are in ANSI format.
    
## Return value

S_OK 
  
> The password modification was successful.
    
MAPI_E_NO_ACCESS 
  
> The old password pointed to by  _lpOldPass_ is invalid. 
    
MAPI_E_NO_SUPPORT 
  
> The status object does not support this operation, as indicated by the absence of the STATUS_CHANGE_PASSWORD flag in the status object's **PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md)) property.
    
## Remarks

Not all status objects support the **IMAPIStatus::ChangePassword** method. It is supported only by service providers that require clients to enter a password. None of the status objects that MAPI implements support the password change operation. 
  
 **ChangePassword** modifies a password programmatically, without user interaction. 
  
## Notes to implementers

Remote transport providers implement **ChangePassword** as specified here. There are no special considerations. 
  
## See also



[PidTagResourceMethods Canonical Property](pidtagresourcemethods-canonical-property.md)
  
[IMAPIStatus : IMAPIProp](imapistatusimapiprop.md)

