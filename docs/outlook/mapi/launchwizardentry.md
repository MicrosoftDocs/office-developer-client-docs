---
title: "LAUNCHWIZARDENTRY"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.LAUNCHWIZARDENTRY
api_type:
- COM
ms.assetid: 5778dffa-f01b-46b3-9c19-862793740918
description: "Last modified: March 09, 2015"
---

# LAUNCHWIZARDENTRY

  
  
**Applies to**: Outlook 
  
Defines a function that starts the Profile Wizard application for the purpose of adding one or more message services to a profile. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiwz.h  <br/> |
|Defined function implemented by:  <br/> |MAPI  <br/> |
|Defined function called by:  <br/> |Client applications  <br/> |
   
```cpp
HRESULT LAUNCHWIZARDENTRY(
  HWND hParentWnd,
  ULONG ulFlags,
  LPCSTR FAR * lppszServiceNameToAdd,
  ULONG cbBufferMax,
  LPSTR lpszNewProfileName
);
```

## Parameters

 _hParentWnd_
  
> [in] A handle to the caller's parent window. If the caller does not have a parent window, the  _hParentWnd_ parameter should be NULL. 
    
 _ulFlags_
  
> [in] Bitmask of flags indicating options for the Profile Wizard. The following flags can be set:
    
MAPI_PW_ADD_SERVICE_ONLY 
  
> The Profile Wizard is to add only the message services listed through the  _lppszServiceNameToAdd_ parameter, and not display its page for selecting message services. 
    
MAPI_PW_FIRST_PROFILE 
  
> The profile to be created is the first one for this workstation. 
    
MAPI_PW_HIDE_SERVICES_LIST 
  
> The Profile Wizard's page for selecting message services should not be displayed. 
    
MAPI_PW_LAUNCHED_BY_CONFIG 
  
> The Profile Wizard was launched by the Control Panel configuration application. 
    
MAPI_PW_PROVIDER_UI_ONLY 
  
> Only the service providers's configuration dialog boxes should be displayed and the Profile Wizard's pages should not appear. This flag can only be set if the MAPI_PW_ADD_SERVICE_ONLY flag is set. 
    
 _lppszServiceNameToAdd_
  
> [in] Pointer to an array of strings that contains the names of the message services to be added to the profile. The array must terminate with a NULL value. 
    
 _cbBufferMax_
  
> [in] Size of the buffer pointed to by the  _lpszNewProfileName_ parameter. 
    
 _lpszNewProfileName_
  
> [out] Pointer to a string buffer where the function based on **LAUNCHWIZARDENTRY** returns the name of the created profile. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_CALL_FAILED 
  
> An error of unexpected or unknown origin prevented the operation from completing. Possibilities include failure to initialize the MAPI subsystem for the Profile Wizard, inability to access the default profile, and an error return from the dialog box.
    
## Remarks

The MAPI implementation of the **LAUNCHWIZARDENTRY** function prototype is the entry point into the MAPI Profile Wizard application. MAPI names this entry point **LaunchWizard**. 
  
When the MAPI_PW_ADD_SERVICE_ONLY flag is set in the  _ulFlags_ parameter, the following rules apply: 
  
- The MAPI_PW_LAUNCHED_BY_CONFIG flag inhibits the welcome page from being displayed. 
    
- The MAPI_PW_HIDE_SERVICES_LIST and MAPI_PW_PROVIDER_UI_ONLY flags are useful only when there is no default profile. In this case these flags determine which Profile Wizard page is to be displayed. 
    
- If a default profile exists, none of the Profile Wizard pages are to be displayed. 
    
- If a default profile exists, only one message service is listed through the  _lppszServiceNameToAdd_ parameter, and that message service is already in the default profile, the Profile Wizard returns S_OK without adding anything to the profile. 
    
For every message service to be added to the profile, the Profile Wizard calls the service's entry point function based on the [MSGSERVICEENTRY](msgserviceentry.md) prototype. For each service provider selected from a message service to be added to the profile, the Profile Wizard calls the provider's entry point function based on the [WIZARDENTRY](wizardentry.md) prototype. During interactive configuration, every user event in the property pages causes the Profile Wizard to call the provider's callback function based on the [SERVICEWIZARDDLGPROC](servicewizarddlgproc.md) prototype. 
  
If a service provider being added to the profile supports the Profile Wizard pages, it must allow programmatic configuration of the profile.
  

