---
title: "Implementing Address Book Provider Logon and Logoff"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: c4a1fb5d-ae23-445b-a6f0-ef430b03fc9a
description: "Last modified: July 23, 2011"
---

# Implementing Address Book Provider Logon and Logoff

**Applies to**: Outlook 2013 | Outlook 2016 
  
Address book providers support session logon and logoff by implementing the methods of the [IABProvider : IUnknown](iabprovideriunknown.md) interface. The ** IABProvider ** interface inherits directly from **IUnknown** and adds only two other methods: **Logon** and **Shutdown**. 
  
## Logoff

MAPI will call your provider's [IABProvider::Logon](iabprovider-logon.md) method at the beginning of every session and whenever your provider is added to the current profile and the client supports dynamic reconfiguration. When MAPI calls the **IABProvider::Logon** method, your address book provider begins its logon process. 
  
**To implement IABProvider::Log**
  
1. Initialize all of the output parameter pointers passed in by MAPI. 
    
2. Call the support object's **IUnknown::AddRef** method to increment its reference count. 
    
3. Call the support object's [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) method to open the section of the profile that contains configuration information about your provider. Pass NULL for the  _lpUID_ parameter and the MAPI_MODIFY flag if you intend to make changes. 
    
4. Call the profile section's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the properties that your provider needs for logon, such as the name of the data file or database table. 
    
5. Check that the properties are all available and valid. If necessary and allowed, display a dialog box to prompt the user to make corrections or additions to invalid or missing information and call the profile section's [IMAPIProp::SetProps](imapiprop-setprops.md) method to save any changes. Some of the common properties that should be available include: 
    
   **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
   **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))
    
   **PR_PROVIDER_DISPLAY** ([PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md))
    
   **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md))
    
   > [!NOTE]
   > Do not set **PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) or **PR_PROVIDER_DLL_NAME** ([PidTagProviderDllName](pidtagproviderdllname-canonical-property.md)). At logon time, these properties are read-only. 
  
6. If one or more configuration properties are unavailable, fail and return the value MAPI_E_UNCONFIGURED.
    
7. Call [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) to register a [MAPIUID](mapiuid.md). Your provider can create a **MAPIUID** by: 
    
   - Calling the [IMAPISupport::NewUID](imapisupport-newuid.md) method. 
    
   - Calling the UUIDGEN.EXE tool to define a GUID that your provider uses to include in one of its header files.
    
8. If desired, save a newly created **MAPIUID** in the current profile by calling the profile section's ** IMAPIProp::SetProps ** method. 
    
9. Release the profile section by calling its **IUnknown::Release** method. 
    
10. Instantiate a new logon object and set the contents of the  _lppABLogon_ parameter to the address of this new object. 
    
Because it is possible for MAPI to call your ** Logon ** method several times during a session, it is wise to support this possibility in your implementation by being able to create multiple logon objects and keep track of each object that is created. Supporting multiple **Logon** calls enables a user of a client application, for example, to log on to a session with different identities or use different delivery destinations. 
  
**Shutdown** is called when the session is ending. MAPI calls your [IABProvider::Shutdown](iabprovider-shutdown.md) method as one of the last tasks involved in shutting down a session. MAPI has released all of your provider's logon objects and, when your provider receives this call, it can assume that this is the last call it will receive. In your implementation of **IABProvider::Shutdown**, perform any final cleanup that you feel is necessary. For example, your provider might call **MAPIDeinitIdle** if it has called **MAPIInitIdle** to use the idle engine during the session or the **IUnknown::Release** method of any objects that have yet to be released. 
  
If your provider has no final cleanup, its implementation can be made up of a single line of code: 
  
```cpp
return S_OK;

```


