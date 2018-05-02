---
title: "Implementing a Service Provider Entry Point Function"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 83ff54c4-86ce-4529-ae45-260dfb763b30
description: "Last modified: March 09, 2015"
 
 
---

# Implementing a Service Provider Entry Point Function

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Every service provider DLL has an entry point function that MAPI calls to load it. Be aware that this entry point function is not the same as [DllMain](http://msdn.microsoft.com/en-us/library/ms682583.aspx), the Win32 DLL entry point function.
  
Depending on the type of your provider, your provider entry point function conforms to a different prototype. MAPI defines different entry point function prototypes for service providers.
  
|**Provider**|**Entry point function prototype**|
|:-----|:-----|
|Message store providers  <br/> |[MSProviderInit](msproviderinit.md) <br/> |
|Transport providers  <br/> |[XPProviderInit](xpproviderinit.md) <br/> |
|Address book providers  <br/> |[ABProviderInit](abproviderinit.md) <br/> |
   
Much of the functionality in these prototypes is the same for all service provider types. 
  
Address book, message store, and transport providers perform the following two main tasks in their entry point functions:
  
1. Check the version of the service provider interface (SPI) to be sure that MAPI is using a version that is compatible with the version that your service provider is using. Use the  _lpulMAPIVer_ parameter, which contains the MAPI SPI version, and the  _lpulProviderVer_ parameter, which contains your SPI version, to perform the check. These parameters are 32-bit unsigned integers composed of three parts: 
    
  - Bits 24 through 31 represent the major version.
    
  - Bits 16 through 23 represent the minor version.
    
  - Bits 0 through 15 represent the update identifier. Although the major version number rarely changes, the minor version number changes whenever MAPI is released and the SPI has changed. The update identifier is the Microsoft internal build version; it is used to track changes during the development process. MAPI defines the CURRENT_SPI_VERSION constant, documented in the Mapispi.h header file, to indicate the present SPI version. Fail your check with the error MAPI_E_VERSION if you are using a version of the SPI that is newer than the version that MAPI is using.
    
2. Create an instance of a provider object. Because your provider can be started and initialized multiple times, you should create a new instance each time this occurs. Providers are started multiple times when they appear in multiple profiles that are in use simultaneously by one or more clients, or when they appear multiple times in a single profile. Just as the entry point function prototype differs depending on the type of your provider, so does the type of provider object. 
    
    If you are writing an address book provider, implement [IABProvider : IUnknown](iabprovideriunknown.md). If you are writing a message store provider, implement [IMSProvider : IUnknown](imsprovideriunknown.md). For more information, see [Loading Message Store Providers](loading-message-store-providers.md).
    
    If you are writing a transport provider, implement [IXPProvider : IUnknown](ixpprovideriunknown.md). For more information, see [Initializing the Transport Provider](initializing-the-transport-provider.md).
    
## See also

#### Concepts

[Starting a Service Provider](starting-a-service-provider.md)

