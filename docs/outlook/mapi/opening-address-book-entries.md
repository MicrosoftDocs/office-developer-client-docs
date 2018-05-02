---
title: "Opening Address Book Entries"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 017a62c0-49c6-47fb-acce-db58e6bb9cc5
description: "Last modified: July 23, 2011"
 
 
---

# Opening Address Book Entries

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
When a client or provider has requested that one of your objects be opened, MAPI calls your provider's [IABLogon::OpenEntry](iablogon-openentry.md) method. MAPI determines that the entry identifier representing the target object belongs to your provider by examining the [MAPIUID](mapiuid.md) portion of the entry identifier and matching it to the **MAPIUID** that your provider registered in the call to **IMAPISupport::SetProviderUID**. MAPI then calls your **OpenEntry** method. Your provider must respond by retrieving the corresponding object — a container, distribution list, or messaging user. 
  
A NULL entry identifier indicates a request to open the address book provider's root container. Clients open the root container to access its hierarchy table and its recipients. Address book providers that only supply templates for creating one-off recipients do not support the **OpenEntry** call for the root container. 
  
 **To implement IABLogon::OpenEntry**
  
1. Check that the entry identifier is a valid identifier that your provider supports. If it is not a valid entry identifier, return MAPI_E_INVALID_ENTRYID. 
    
2. Check the flag that is passed in with the  _ulFlags_ parameter. If MAPI has passed in MAPI_MODIFY and your provider does not allow its objects to be modified, fail and return the MAPI_E_ACCESS_DENIED error value. 
    
3. Check that the interface requested in the  _lpInterface_ parameter is valid for the type of object your provider has been asked to open. If an invalid parameter has been passed in, fail and return the MAPI_E_INTERFACE_NOT_SUPPORTED error value. 
    
4. If the  _cbEntryID_ parameter is zero, this is a request to open your provider's root container. Create the root container and return a pointer to its **IABContainer** interface implementation. 
    
5. If your provider implements several logon objects, each with its own registered **MAPIUID**, map the **MAPIUID** contained in the entry identifier with the appropriate logon object. 
    
6. Determine which type of object the entry identifier represents: a messaging user, distribution list, or container belonging to your provider or a one-off messaging user or distribution list so that the appropriate value can be set for the  _lpulObjectType_ parameter. 
    
7. Create the object of the appropriate type and set the following basic properties:
    
    **PR_DISPLAY_TYPE** ( [PidTagDisplayType](pidtagdisplaytype-canonical-property.md))
    
    **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md))
    
    **PR_OBJECT_TYPE** ( [PidTagObjectType](pidtagobjecttype-canonical-property.md))
    
    **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
    Calculate **PR_EMAIL_ADDRESS** ( [PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) and **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) from information in the entry identifier.
    
8. Return a pointer to the interface implementation for the object. 
    

