---
title: "IProviderAdminCreateProvider"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProviderAdmin.CreateProvider
api_type:
- COM
ms.assetid: 80c1449a-6cd9-4b93-a300-395979894b71
description: "Last modified: July 23, 2011"
---

# IProviderAdmin::CreateProvider

  
  
**Applies to**: Outlook 
  
Adds a service provider to the message service. 
  
```
HRESULT CreateProvider(
  LPSTR lpszProvider,
  ULONG cValues,
  LPSPropValue lpProps,
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  MAPIUID FAR * lpUID
);
```

## Parameters

 _lpszProvider_
  
> [in] A pointer to the name of the provider to add.
    
 _cValues_
  
> [in] The count of property values pointed to by the  _lpProps_ parameter. 
    
 _lpProps_
  
> [in] A pointer to a property value array that describes the properties of the provider to add.
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows this method displays. The  _ulUIParam_ parameter is used if the MAPI_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the provider addition. The following flags can be set:
    
MAPI_DIALOG 
  
> Displays a dialog box to prompt for configuration information.
    
MAPI_UNICODE 
  
> The provider name and string properties are in Unicode format. If the MAPI_UNICODE flag is not set, these strings are in ANSI format.
    
 _lpUID_
  
> [out] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier that represents the provider to add. 
    
## Return value

S_OK 
  
> The provider was successfully added to the message service.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

The **IProviderAdmin::CreateProvider** method adds a service provider to the message service. The  _lpszProvider_ parameter must point to the name of a provider that belongs to the message service. **CreateProvider** does not verify whether the name matches the name of a provider in the service; if the passed name does not match a service name, the call succeeds, but the results are unpredictable. Most message services do not allow providers to be added or deleted while the profile is in use. 
  
After all of the available information about the service provider has been added to the profile from the Mapisvc.inf file, **CreateProvider** calls the message service's entry point function with the  _ulContext_ parameter set to MSG_SERVICE_PROVIDER_CREATE. If MAPI_DIALOG is set in the **CreateProvider** method's  _ulFlags_ parameter, the values in the  _ulUIParam_ and  _ulFlags_ parameters are also passed to the entry point function. These additional parameters enable the service provider to display its property sheet so the user can enter configuration settings. 
  
## See also

#### Reference

[MAPIUID](mapiuid.md)
  
[MSGSERVICEENTRY](msgserviceentry.md)
  
[SPropValue](spropvalue.md)
  
[IProviderAdmin : IUnknown](iprovideradminiunknown.md)

