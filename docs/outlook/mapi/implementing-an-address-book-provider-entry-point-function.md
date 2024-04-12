---
title: "Implementing an Address Book Provider Entry Point Function"
description: "Describes how to implement an address book provider entry point function, which instantiates a provider object and returns to MAPI a pointer to that object."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 9375b351-1c84-4728-bcdf-e3e7a44820ed
 
 
---

# Implementing an Address Book Provider Entry Point Function

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
When a client application calls [MAPILogonEx](mapilogonex.md) to begin a session using a profile that contains your address book provider, MAPI loads your provider and all others that are part of the profile. MAPI learns of the name of your provider's entry point function by looking in the profile. Remember that this function is not the same as a DLL entry point function; see the documentation for **DllMain** in the Win32 documentation. 
  
There are several entries, some of which must appear in the mapisvc.inf configuration file, that are included in the profile section of every address book provider. The following table lists these profile section entries and whether or not the mapisvc.inf file must include them.
  
|**Profile section entry**|**mapisvc.inf requirement**|
|:-----|:-----|
|PR_DISPLAY_NAME= _string_ <br/> |Optional  <br/> |
|PR_PROVIDER_DISPLAY= _string_ <br/> |Required  <br/> |
|PR_PROVIDER_DLL_NAME= _DLL filename_ <br/> |Required  <br/> |
|PR_RESOURCE_TYPE= _long_ <br/> |Required  <br/> |
|PR_RESOURCE_FLAGS= _bitmask_ <br/> |Optional  <br/> |
   
Your address book provider can place this information into a profile directly by calling its profile section's [IMAPIProp::SetProps](imapiprop-setprops.md) method or indirectly by modifying MAPISVC.INF. Profiles are built using the relevant information in MAPISVC.INF for the selected service providers or message services. For more information about the organization and contents of MAPISVC.INF, see [File Format of MapiSvc.inf](file-format-of-mapisvc-inf.md).
  
The name of your address book provider's DLL entry point function must be [ABProviderInit](abproviderinit.md) and it must conform to the **ABProviderInit** prototype. Perform the following tasks in your provider's DLL entry point function: 
  
- Check the version of the service provider interface (SPI) to make sure MAPI is using a version that is compatible with the version that your address book provider is using.
    
- Instantiate an address book provider object.
    
Do not call either **MAPIInitialize** or **MAPIUninitialize** in this function. 
  
The DLL entry point function instantiates a provider object and returns to MAPI a pointer to that object. 
  

