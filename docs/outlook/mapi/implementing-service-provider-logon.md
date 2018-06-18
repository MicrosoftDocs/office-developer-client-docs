---
title: "Implementing Service Provider Logon"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 3d3c309f-fe60-43a9-beda-16b09ec769db
description: "Last modified: July 23, 2011"
---

# Implementing Service Provider Logon

**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI calls a method in your provider object to begin the logon process by using the pointer that you return from your entry point function. The method varies as follows, depending on the type of your service provider:
  
- [IABProvider::Logon](iabprovider-logon.md) for address book providers 
    
- [IMSProvider::Logon](imsprovider-logon.md) for message store providers 
    
- [IXPProvider::TransportLogon](ixpprovider-transportlogon.md) for transport providers 
    
Perform the following tasks in whatever logon method you implement:
  
1. Increment the reference count on the support object that is passed as an input parameter by calling its [IUnknown::AddRef](http://msdn.microsoft.com/en-us/library/ms691379%28v=VS.85%29.aspx) method. 
    
2. Call the support object's [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) method to access your profile section. 
    
3. Call the profile section's [IMAPIProp::SetProps](imapiprop-setprops.md) method to set the following properties: 
    
  - **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
  - **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))
    
  - **PR_PROVIDER_DISPLAY** ([PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md))
    
  - **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md))
    
  > [!NOTE]
  > Do not attempt to set the profile section's **PR_RESOURCE_FLAGS** or **PR_PROVIDER_DLL_NAME** properties. At logon time, these properties are read-only. 
  
4. Check that the properties you need for configuration are either stored in the profile or are available from the user. For more information about checking your configuration, see [Verifying Service Provider Configuration](verifying-service-provider-configuration.md).
    
5. Call the support object's [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) method to register a unique identifier, or [MAPIUID](mapiuid.md), if your provider is an address book or message store provider. Transport providers register **MAPIUID** structures when MAPI calls their [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method. For more information about registering a **MAPIUID**, see [Registering Service Provider Unique Identifiers](registering-service-provider-unique-identifiers.md).
    
6. Instantiate a logon object and return with one of the following values:
    
  - S_OK to indicate a successful logon.
    
  - MAPI_E_UNCONFIGURED to indicate that one or more of the configuration properties were unavailable.
    
  - MAPI_E_USER_CANCEL to indicate that the user canceled the configuration dialog box, causing configuration properties to be unavailable.
    
  - MAPI_E_FAILONEPROVIDER to indicate that your provider could not be configured, but that MAPI should allow it to be used regardless. Logon methods should return this value to report a nonfatal error, such as when the provider requires a password and cannot prompt the user for it because the user interface is disabled. 
    
The preceding list of tasks describes a minimum implementation for a service provider logon method. You can include additional functionality, if necessary. For example, some providers call [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) to update the status table in their logon method. 
  
> [!NOTE]
> To achieve the best performance at logon time, avoid calling either [IMAPISupport::PrepareSubmit](imapisupport-preparesubmit.md) or [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md). Before these calls can complete and return control to your logon method, the MAPI spooler must be started. 
  
## See also

- [Starting a Service Provider](starting-a-service-provider.md)

