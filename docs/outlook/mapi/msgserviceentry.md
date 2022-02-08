---
title: "MSGSERVICEENTRY"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.MSGSERVICEENTRY
api_type:
- COM
ms.assetid: 655774a6-588c-44c7-903b-4497b7eccbc2
description: "Last modified: March 09, 2015"
---

# MSGSERVICEENTRY

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Defines a prototype for a message service entry point function to support message service configuration. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Defined function implemented by:  <br/> |Message services  <br/> |
|Defined function called by:  <br/> |MAPI  <br/> |
   
```cpp
HRESULT MSGSERVICEENTRY(
  HINSTANCE hInstance,
  LPMALLOC lpMalloc,
  LPMAPISUP lpMAPISup,
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  ULONG ulContext,
  ULONG cValues,
  LPSPropValue lpProps,
  LPPROVIDERADMIN lpProviderAdmin,
  LPMAPIERROR FAR * lppMapiError
);
```

## Parameters

 _hInstance_
  
> [in] Handle of the instance of the service providerDLL. The handle is typically used to retrieve resources. 
    
 _lpMalloc_
  
> [in] Pointer to a memory allocator object exposing the OLE **IMalloc** interface. The message service may need to use this allocation method when working with certain interfaces such as **IStream**. 
    
 _lpMAPISup_
  
> [in] Pointer to an [IMAPISupport : IUnknown](imapisupportiunknown.md) interface implementation. 
    
 _ulUIParam_
  
> [in] An implementation-specific value used for passing user interface information to a function or zero. The  _ulUIParam_ parameter is the parent window handle for the configuration dialog box and is of type HWND (cast to a ULONG_PTR). A value of zero indicates that there is no parent window. 
    
 _ulFlags_
  
> [in] Bitmask of flags indicating options for the service entry function. The following flags can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
MSG_SERVICE_UI_READ_ONLY 
  
> The service's configuration user interface should display the current configuration but not allow the user to change it. 
    
SERVICE_UI_ALLOWED 
  
> Permits a configuration dialog box to be displayed if necessary. When the SERVICE_UI_ALLOWED flag is set, the dialog box should be displayed only if the _lpProps_ property value array is empty or does not contain a valid configuration. If SERVICE_UI_ALLOWED is not set, a dialog box might still be displayed if the SERVICE_UI_ALWAYS flag is set. 
    
UI_CURRENT_PROVIDER_FIRST 
  
> Requests that the configuration dialog box for the active provider be displayed on top of other dialog boxes. 
    
SERVICE_UI_ALWAYS 
  
> Requires the message service to display a configuration dialog box. If the SERVICE_UI_ALWAYS flag is not set, a configuration dialog box might still be displayed if the SERVICE_UI_ALLOWED flag is set and valid configuration information is not available from the  _lpProps_ property value array. Either SERVICE_UI_ALLOWED or SERVICE_UI_ALWAYS must be set to allow a user interface to be displayed. 
    
 _ulContext_
  
> [in] The configuration operation that MAPI is currently performing. The  _ulContext_ parameter will contain one of the following values: 
    
MSG_SERVICE_CONFIGURE 
  
> Changes to the service's configuration should be made in the profile. If the SERVICE_UI_ALWAYS flag is set, the service should display its configuration dialog box. The dialog box should also be displayed if the SERVICE_UI_ALLOWED flag is set and the  _lpProps_ parameter is empty or does not contain valid configuration data. If  _lpProps_ contains valid data, no dialog box should be displayed and the service should use this data for making the configuration change. 
    
MSG_SERVICE_CREATE 
  
> The service is being added to a profile. If either the SERVICE_UI_ALWAYS or SERVICE_UI_ALLOWED flag is set, the service should display its configuration dialog box. If neither flag is set, the service should fail. 
    
MSG_SERVICE_DELETE 
  
> The service is being removed from a profile. After receiving this event, the service should return S_OK.
    
MSG_SERVICE_INSTALL 
  
> The service has been installed to the user's workstation from a network, floppy disk, or other external medium. After receiving this event, the service usually returns S_OK. 
    
MSG_SERVICE_PROVIDER_CREATE 
  
> Requests that the service create an additional instance of a provider. If the service supports this operation, it should call [IProviderAdmin::CreateProvider](iprovideradmin-createprovider.md). If the service does not support this operation, it can return MAPI_E_NO_SUPPORT. 
    
MSG_SERVICE_PROVIDER_DELETE 
  
> Requests that the service delete a provider instance. If the service supports this operation, it should call [IProviderAdmin::DeleteProvider](iprovideradmin-deleteprovider.md). If the service does not support this operation, it can return MAPI_E_NO_SUPPORT.
    
MSG_SERVICE_UNINSTALL 
  
> The service is being removed. After receiving this event, the service can perform any cleanup tasks that should be done before the service ends and then return with a success value. If the user cancels the removal, the service should return MAPI_E_USER_CANCEL. 
    
 _cValues_
  
> [in] Count of property values in the array pointed to by the  _lpProps_ parameter. The value of the  _cValues_ parameter is zero if MAPI is passing no property values. 
    
 _lpProps_
  
> [in] Pointer to an optional array of [SPropValue](spropvalue.md) structures indicating values for provider-supported properties that the function will use in configuring the message service. The function only uses this parameter if the _ulContext_ parameter is set to MSG_SERVICE_CONFIGURE. This parameter is commonly used to pass the path to a file for a file-based service, such as a personal address book service. If the MSG_SERVICE_CONFIGURE flag is not passed in the _ulFlags_ parameter, the  _lpProps_ parameter must be zero. 
    
 _lpProviderAdmin_
  
> [in] Pointer to an [IProviderAdmin:IUnknown](iprovideradminiunknown.md) interface that the function can use to locate profile sections for a specific provider in the current message service. 
    
 _lppMapiError_
  
> [out] Pointer to a [MAPIERROR](mapierror.md) structure. The structure is allocated with the [MAPIAllocateBuffer](mapiallocatebuffer.md) function. All members are optional, although most structures will contain a valid error message string in the _lpszError_ member. If the  _lpszComponent_ or  _lpszError_ members of the structure are present, their memory must eventually be freed by a single call to [MAPIFreeBuffer](mapifreebuffer.md) on the base structure. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_UNCONFIGURED 
  
> The service provider has not been configured. 
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
MAPI_E_NO_SUPPORT 
  
> The provider either does not support changes to its objects or does not support notification of changes. 
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation only supports Unicode.
    
## Remarks

A function defined using the **MSGSERVICEENTRY** function prototype enables message services to configure themselves or to perform other service-specific actions. The function primarily furnishes a dialog box in which the user can change settings specific to the message service. It can also support programmatic configuration by using the property value array passed in the _lpProps_ parameter. Programmatic configuration is optional unless the service supports the Profile Wizard, for which it is required. 
  
MAPI calls this entry point from the Control Panel application or in response to a client application calling [IMsgServiceAdmin::CreateMsgService](imsgserviceadmin-createmsgservice.md) or [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md). 
  
MAPI places no restriction on the function name that a message service uses for the **MSGSERVICEENTRY** prototype but prefers the name **ServiceEntry**. There is no restriction on the ordinal for the function, and a single provider DLL can contain more than one function. However, only one of the functions can be named **ServiceEntry**. 
  
A message service can use the [BuildDisplayTable](builddisplaytable.md) function and the [IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md) method to simplify configuration dialog box implementation. 
  
It is possible for a user to cancel a MSG_SERVICE_UNINSTALL operation. In this case, the **ServiceEntry** function should check with the user to verify that the service should not be removed and return MAPI_E_USER_CANCEL if the service remains installed. 
  
A function based on the **MSGSERVICEENTRY** prototype returns one of the HRESULT values listed. MAPI forwards this value when responding to a client's call to [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md). 
  
Message services that export a service entry function must include the **PR_SERVICE_DLL_NAME** ([PidTagServiceDllName](pidtagservicedllname-canonical-property.md)) and **PR_SERVICE_ENTRY_NAME** ([PidTagServiceEntryName](pidtagserviceentryname-canonical-property.md)) properties in the message service section of MAPISVC.INF. 
  

