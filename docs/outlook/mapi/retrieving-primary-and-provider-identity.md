---
title: "Retrieving Primary and Provider Identity"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: d81bb81d-1708-4a8d-a4d5-c3ba087db9b7
 
 
---

# Retrieving Primary and Provider Identity

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Service providers, typically address book providers, have the option of supplying an identity that can be used to represent the session in a variety of situations. Three properties describe a provider's identity:
  
- **PR_IDENTITY_ENTRYID** ([PidTagIdentityEntryId](pidtagidentityentryid-canonical-property.md)) 
    
- **PR_IDENTITY_DISPLAY** ([PidTagIdentityDisplay](pidtagidentitydisplay-canonical-property.md)) 
    
- **PR_IDENTITY_SEARCH_KEY** ([PidTagIdentitySearchKey](pidtagidentitysearchkey-canonical-property.md)) 
    
These properties are set to the entry identifier, display name, and search key of the corresponding identity object, which is typically a messaging user. Providers that supply an identity also set the STATUS_PRIMARY_IDENTITY flag in their **PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) property.
  
Depending on your needs, you might use a particular provider's identity or the primary identity for the session. You can use a provider's identity also for display purposes or to retrieve properties, such as **PR_RESOURCE_PATH** ([PidTagResourcePath](pidtagresourcepath-canonical-property.md)). **PR_RESOURCE_PATH**, if set, contains the path to files used or created by the provider. Retrieve the **PR_RESOURCE_PATH** property for the provider supplying the primary identity when you want to locate files that pertain to the user of the session. 
  
 **To retrieve the identity of a specific provider**
  
1. Call [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to access the status table. 
    
2. Build a restriction using an [SPropertyRestriction](spropertyrestriction.md) structure to match the **PR_PROVIDER_DLL_NAME** ([PidTagProviderDllName](pidtagproviderdllname-canonical-property.md)) column with the name of the specified provider. 
    
3. Call [IMAPITable::FindRow](imapitable-findrow.md) to locate the provider's row. The provider's identity will be stored in the **PR_IDENTITY_ENTRYID** column, if it exists. 
    
 **To retrieve the primary identity for a session**
  
- Call [IMAPISession::QueryIdentity](imapisession-queryidentity.md). **QueryIdentity** bases session identity on the existence of the STATUS_PRIMARY_IDENTITY value in the **PR_RESOURCE_FLAGS** column for one of the rows in the status table. If none of the status rows have this value set, **QueryIdentity** assigns identity to the first service provider that sets the three PR_IDENTITY properties. If no service provider supplies an identity, **QueryIdentity** returns MAPI_W_NO_SERVICE. When this happens, you should create a character string to represent a generic user that can serve as the primary identity. 
    
 **To explicitly set the primary identity for a session**
  
- Call [IMsgServiceAdmin::SetPrimaryIdentity](imsgserviceadmin-setprimaryidentity.md). Pass the **MAPIUID** for the target service provider. 
    

