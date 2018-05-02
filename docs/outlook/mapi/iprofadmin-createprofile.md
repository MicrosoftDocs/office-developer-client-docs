---
title: "IProfAdminCreateProfile"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProfAdmin.CreateProfile
api_type:
- COM
ms.assetid: 10cda14a-8f93-41e0-b1fb-500098bdc392
description: "Last modified: July 23, 2011"
---

# IProfAdmin::CreateProfile

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Creates a new profile.
  
```
HRESULT CreateProfile(
  LPSTR lpszProfileName,
  LPSTR lpszPassword,
  ULONG_PTR ulUIParam,
  ULONG ulFlags
);
```

## Parameters

 _lpszProfileName_
  
> [in] A pointer to the name of the new profile.
    
 _lpszPassword_
  
> [in] A pointer to the password of the new profile. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows that this method displays.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the profile is created. The following flags can be set:
    
MAPI_DEFAULT_SERVICES 
  
> MAPI should populate the new profile with the message services that are included in the [Default Services] section of the Mapisvc.inf file.
    
MAPI_DIALOG 
  
> The configuration property sheets of each of the providers in the message services to be added can be displayed. 
    
## Return value

S_OK 
  
> The new profile was created.
    
MAPI_E_NO_ACCESS 
  
> The specified new profile already exists.
    
## Remarks

The **IProfAdmin::CreateProfile** method creates a new profile. 
  
## Notes to Callers

You can call **CreateProfile** at application installation time or at any time during a session. When this method is called at installation time, many of the configuration settings come from the Mapisvc.inf configuration file. When this method is called during an active session, the settings come from the user who is prompted through a series of property sheets. 
  
If the MAPI_DEFAULT_SERVICES flag is set in the  _ulFlags_ parameter, **CreateProfile** calls the message service entry point function for each message service in the [Default Services] section in the Mapisvc.inf file. Each message service entry point function is called with the  _ulContext_ parameter set to MSG_SERVICE_CREATE. 
  
If both the MAPI_DIALOG and MAPI_DEFAULT_SERVICES flags are set, the values in the  _ulUIParam_ and  _ulFlags_ parameters are also passed to the message service entry point function. The message service entry point functions are called only after all available information from the Mapisvc.inf file has been added to the profile. 
  
The name of the new profile and its password can be up to 64 characters in length and can include the following characters:
  
- All alphanumeric characters, including accent characters and the underscore character.
    
- Embedded spaces, but not leading or trailing spaces.
    
The  _lpszPassword_ parameter must be NULL or a pointer to a zero-length string. 
  
## See also

#### Reference

[IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md)
  
[IMsgServiceAdmin::CreateMsgService](imsgserviceadmin-createmsgservice.md)
  
[MSGSERVICEENTRY](msgserviceentry.md)
  
[IProfAdmin : IUnknown](iprofadminiunknown.md)

