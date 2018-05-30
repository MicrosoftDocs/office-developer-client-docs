---
title: "WIZARDENTRY"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.WIZARDENTRY
api_type:
- COM
ms.assetid: e807c6b5-06cd-4ade-9d9e-69ba6abd1614
description: "Last modified: March 09, 2015"
---

# WIZARDENTRY

  
  
**Applies to**: Outlook 
  
Defines a service provider entry point function which the Profile Wizard calls to retrieve enough information to display the provider's configuration property sheets. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiwz.h  <br/> |
|Defined function implemented by:  <br/> |Service providers  <br/> |
|Defined function called by:  <br/> |MAPI Profile Wizard  <br/> |
   
```cpp
ULONG WIZARDENTRY(
  HINSTANCE hProviderDLLInstance,
  LPSTR FAR * lpcsResourceName,
  DLGPROC FAR * lppDlgProc,
  LPMAPIPROP lpMAPIProp,
  LPMAPISUPPORTOBJECT lpMapiSupportObject
);
```

## Parameters

 _hProviderDLLInstance_
  
> [in] Instance handle of the service provider's DLL. 
    
 _lpcsResourceName_
  
> [out] Pointer to a string that contains the full name of the dialog resource that should be displayed by the Profile Wizard during configuration. The maximum size of the string, including the NULL terminator, is 32 characters. 
    
 _lppDlgProc_
  
> [out] Pointer to a standard Windows dialog box procedure that will be called by the Profile Wizard to notify the provider of various events. 
    
 _lpMAPIProp_
  
> [in] Pointer to a property interface implementation that provides access to the configuration properties. 
    
 _lpMapiSupportObject_
  
> [in] Pointer to the MAPI support object applicable to this session.
    
## Return value

S_OK 
  
> The service provider's **WIZARDENTRY** function was called successfully. 
    
MAPI_E_CALL_FAILED 
  
> An error of unexpected or unknown origin prevented the operation from completing.
    
## Remarks

The Profile Wizard calls the **WIZARDENTRY** based function when it is ready to display the service provider's configuration user interface. When the Profile Wizard is finished configuring all providers, it writes the configuration properties to the profile by calling [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md). 
  
## Notes to implementers

The name of the **WIZARDENTRY** based function must be placed in the WIZARD_ENTRY_NAME entry in MAPISVC.INF. 
  
The resource name is that of the dialog resource that will be rendered in the pane of the Profile Wizard. The resource that is passed back needs to contain all the pages in a single dialog resource. When the Profile Wizard receives this resource, it ignores the dialog style, but not the control styles, and creates all the controls as children of the Profile Wizard page. All controls are initially hidden. Providers should make sure that the coordinates for their controls are zero or zero-based, and that they do not exceed a maximum width of 200 dialog units and a maximum height of 150 dialog units. Control identifiers below 400 are reserved for the Profile Wizard. The Profile Wizard displays the provider's title in bold text above the provider's user interface. 
  
The property interface pointer supplied in the  _lpMAPIProp_ parameter should be retained by the provider for future reference. The Profile Wizard deals with only the most basic set of properties, and the provider can use the property interface implementation to include additional properties. During configuration, providers should add their configuration properties to the object implementing the property interface. After all providers have been configured, the Profile Wizard adds these properties to the profile. 
  
For more information about how to use this function, see [Supporting Message Service Configuration](supporting-message-service-configuration.md). 
  

