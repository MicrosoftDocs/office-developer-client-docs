---
title: "Support Object Overview"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 5b062891-39ab-4334-9706-5b376719d5e4
description: "Last modified: July 23, 2011"
---

# Support Object Overview

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
MAPI furnishes a support object, an object that implements the [IMAPISupport : IUnknown](imapisupportiunknown.md) interface, for all service providers during logon and for all message services during configuration. 
  
Support objects are not accessible by clients; they are implemented by MAPI and called only by service providers. The **IMAPISupport** interface is specified in the Mapispi.h header file. Its identifier is IID_IMAPISup and its pointer type is LPMAPISUP. No MAPI properties are exposed by support objects. 
  
A provider can be given one or more support objects, depending on the number of times MAPI logs the provider on or the number of times the provider's message service entry function is called. Typically, a provider will be logged on at least once per session. Address book and transport providers are logged on every time a client starts a session with a profile entry that requests them. Message store providers are logged on every time a client calls the [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) method. 
  
In the case of multiple logons in a session, you can choose either to retain and use each support object separately or to retain and use only the first, discarding each subsequent support object. To retain a support object, call its **IUnknown::AddRef** method. Calling **AddRef** on a support object that you want to retain throughout a session is extremely important; if the call is not made, MAPI releases the support object and frees its memory. 
  
The purpose of the support object is to provide implementations for a fairly large number of methods commonly used by the providers. Each support object also contains contextual data specific to its own instance, such as the session the provider is running in, the profile section the provider is using, and error information for the session. 
  
There are four different types of support objects: one for each major provider type (address book, message store, and transport) and one for configuration support. 
  
MAPI customizes each support object by including implementations of methods that are relevant for its usage. Implementations of some methods, such as [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md), are included in all support objects. Implementations of other methods, such as [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md), apply only to particular support objects. Only message store and transport providers can use this method; when an address book provider or a message service try to call it, MAPI returns MAPI_E_NO_SUPPORT.
  
Support objects can be used to accomplish many tasks, such as the following:
  
- Accessing a profile section.
    
- Copying folders or messages. For more information, see [Copying or Moving a Message or a Folder](copying-or-moving-a-message-or-a-folder.md).
    
- Accessing objects that belong to other providers. For more information, see [Supporting Object Access and Comparison](supporting-object-access-and-comparison.md). 
    
- Handling event notification. For more information, see [Supporting Event Notification](supporting-event-notification.md).
    
- Allocating and freeing memory.
    
- Obtaining a unique identifier.
    
- Invalidating objects.
    
- Handling errors.
    
- Registering message preprocessors. 
    
- Preparing message delivery reports. 
    
At logon time, MAPI calls the logon method of each service provider's provider object. For address book providers, MAPI calls [IABProvider::Logon](iabprovider-logon.md). For message store providers, MAPI calls [IMSProvider::Logon](imsprovider-logon.md). For transport providers, MAPI calls [IXPProvider::TransportLogon](ixpprovider-transportlogon.md). MAPI passes a pointer to the appropriate support object in one of the parameters to this method. The logon method in turn instantiates a logon object, passing it the support object pointer. The logon object calls the support object's **IUnknown::AddRef** method to retain it, if necessary. For more information about the logon process for service providers, see [Starting a Service Provider](starting-a-service-provider.md).
  
When a client logs off, MAPI calls the logon object's logoff method. The logoff method calls the support object's **IUnknown::Release** method to indicate that the provider no longer intends to call any of the support methods. As with logon, the logoff methods have slightly different names. The [IABLogon](iablogoniunknown.md) and [IMSLogon](imslogoniunknown.md) interfaces have **Logoff** methods; the [IXPLogon](ixplogoniunknown.md) interface has a [TransportLogoff](ixplogon-transportlogoff.md) method. 
  
Message service entry point functions are called when a logon attempt fails with the error MAPI_E_UNCONFIGURED or when a client initiates a configuration request. MAPI instantiates a configuration support object and calls the message service entry point function for either the unconfigured provider or the provider whose configuration is about to change. Unlike the other support objects, configuration support objects are valid only until the entry point function returns; message services do not call these objects' **AddRef** methods to retain them. 
  
Typically, MAPI makes calls to a provider's message service entry point function, but sometimes a provider is asked to make the call. This can occur when a client calls a provider's [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) method to prompt the provider to display its configuration property sheet. **SettingsDialog** should call [IMAPISupport::GetSvcConfigSupportObj](imapisupport-getsvcconfigsupportobj.md) to obtain a configuration support object that it can pass to the message service entry point function. 
  
The [IMAPISupport::GetMemAllocRoutines](imapisupport-getmemallocroutines.md) method is available for determining the addresses of the memory allocation and deallocation functions without having to link with MAPI. Using **GetMemAllocRoutines** also makes it easier to trace memory leaks by surrounding the allocation function calls with debugging code. If you call **GetMemAllocRoutines**, as is recommended, do so before calling the [CreateIProp](createiprop.md) function, which requires the allocation function addresses as parameters. 
  
When you need to create a new address book or message store object, create and set a search key for the object in its **PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md)) property. Call [IMAPISupport::NewUID](imapisupport-newuid.md) to obtain a unique identifier to use in building a search key. Do not use your own hard-coded [MAPIUID](mapiuid.md). A provider's **MAPIUID** should be used only for entry identifiers. For more information about constructing search keys, see [MAPI Record and Search Keys](mapi-record-and-search-keys.md).
  
A client application can sometimes release an object without releasing one or more of its affiliated objects. In such a case, a provider may need to render an unreleased object unusable. To do this, the provider frees all of the resources connected with the object and then calls [IMAPISupport::MakeInvalid](imapisupport-makeinvalid.md) to invalidate the object's vtable. **MakeInvalid** replaces the vtable's **IUnknown** methods ( **QueryInterface**, **AddRef**, and **Release**) with standard MAPI implementations and causes all other methods to return MAPI_E_INVALID_OBJECT. **MakeInvalid** also frees all the object's memory other than the vtable. 
  
## See also

#### Concepts

[MAPI Service Providers](mapi-service-providers.md)

