---
title: "Starting a Service Provider"
 
 
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: c4b61cc3-d9fe-4616-a05c-d1e4096b5abd
description: "Last modified: December 07, 2015"
---

# Starting a Service Provider

 **Last modified:** December 07, 2015 
  
 * **Applies to:** Outlook * 
  
At some point after a client starts a session with MAPI, your service provider will be started. Transport providers are started when a client makes a request for their services. Address book and message store providers are started during the client's logon process.
  
A client calls [IMAPISession::OpenAddressBook](imapisession-openaddressbook.md) to load each of the address book providers included in the profile and [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) to load a specific message store provider. Address book providers that are part of a message service are started before any of the other providers in the service. 
  
MAPI starts each service provider in the active profile by doing the following:
  
- Locating the name of its DLL in the profile. You are required to register the name of your provider DLL in the Mapisvc.inf configuration file to ensure that it appears in the profile. When your service provider is added to a profile, either individually or as part of a message service, all of the **[Service Provider]** sections from Mapisvc.inf that apply to your provider are copied into the profile. For more information about the structure of Mapisvc.inf, see [File Format of MapiSvc.inf](file-format-of-mapisvc-inf.md).
    
- Calling the Windows API function **LoadLibrary** to load the DLL. Because MAPI calls **LoadLibrary** either every time it uses a service provider DLL (regardless of whether it has already been loaded) or only the first time, your service provider must not make assumptions about the number of times that it will be loaded. For every call to **LoadLibrary**, MAPI makes a call to the Windows API function **FreeLibrary** when a service provider DLL is no longer needed. 
    
- Calling the entry point function for the provider. MAPI calls your provider's entry point function to initiate the logon process. Entry point functions ensure that you are using a version of the service provider interface (SPI) that is compatible with the version being used by MAPI. These functions also return pointers to newly created provider objects. For more information about creating an entry point function for your provider, see [Implementing a Service Provider Entry Point Function](implementing-a-service-provider-entry-point-function.md).
    
## See also

#### Concepts

[MAPI Service Providers](mapi-service-providers.md)

