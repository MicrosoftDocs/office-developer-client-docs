---
title: "IProfAdminAdminServices"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProfAdmin.AdminServices
api_type:
- COM
ms.assetid: 87235fd2-6527-41a1-98ba-b951632a1c81
description: "Last modified: March 09, 2015"
---

# IProfAdmin::AdminServices

  
  
**Applies to**: Outlook 
  
Provides access to a message service administration object for making changes to the message services in a profile.
  
```cpp
HRESULT AdminServices(
  LPSTR lpszProfileName,
  LPSTR lpszPassword,
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPSERVICEADMIN FAR * lppServiceAdmin
);
```

## Parameters

 _lpszProfileName_
  
> [in] A pointer to the name of the profile to be modified. The  _lpszProfileName_ parameter must not be NULL. 
    
 _lpszPassword_
  
> [in] Always NULL. 
    
 _ulUIParam_
  
> [in] A handle of the parent window for any dialog boxes or windows that this method displays.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the retrieval of the message service administration object. The following flags can be set:
    
MAPI_DIALOG 
  
> Enables the display of a user interface. 
    
MAPI_UNICODE 
  
> The profile name is in Unicode format. If the MAPI_UNICODE flag is not set, the name is in ANSI format.
    
 _lppServiceAdmin_
  
> [out] A pointer to a pointer to a message service administration object.
    
## Return value

S_OK 
  
> The message service administration object was successfully returned.
    
MAPI_E_LOGON_FAILED 
  
> The specified profile does not exist, or the password was wrong and a dialog box could not be displayed to the user to request the correct password because MAPI_DIALOG was not set in  _ulFlags_.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

The **IProfAdmin::AdminServices** method provides access to a message service administration object for making configuration changes to the message services in a profile. 
  
 The  _lpszPassword_ parameter must be NULL or a pointer to a zero-length string. 
  
## Notes to callers

Although you can retrieve an [IMsgServiceAdmin](imsgserviceadminiunknown.md) pointer by calling either this method or [IMAPISession::AdminServices](imapisession-adminservices.md), call **IProfAdmin::AdminServices** if you have strictly a configuration client and offer no messaging features. **IProfAdmin::AdminServices** does not create a session object and does not load any service providers, which enhances performance. 
  
You cannot use **IProfAdmin::AdminServices** to create a profile. Therefore, you must specify an existing valid profile in  _lpszProfileName_. If the specified profile does not exist, **IProfAdmin::AdminServices** returns MAPI_E_LOGON_FAILED. 
  
The name of the profile can be up to 64 characters in length and can include the following characters:
  
- All alphanumeric characters, including accent characters and the underscore character. 
    
- Embedded spaces, but not leading or trailing spaces.
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProfileFunctions.cpp  <br/> | HrAddServiceToProfile  <br/> |MFCMAPI uses the **IProfAdmin::AdminServices** method to open a message service administration object for the selected profile to add services.  <br/> |
   
## See also



[IMAPISession::AdminServices](imapisession-adminservices.md)
  
[IProfAdmin : IUnknown](iprofadminiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

