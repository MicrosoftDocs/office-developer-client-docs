---
title: "Adding Address Book Entries"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 63444a65-d56a-4dbd-9aa6-e60f18ba8104
description: "Last modified: July 23, 2011"
 
 
---

# Adding Address Book Entries

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
To add a messaging user or distribution list to a container, a client calls [IAddrBook::NewEntry](iaddrbook-newentry.md) or a provider calls [IMAPISupport::NewEntry](imapisupport-newentry.md) with the entry identifier of the target container in the  _lpEIDContainer_ parameter. MAPI in turn calls the container's [IABContainer::CreateEntry](iabcontainer-createentry.md) method to create the entry using a one-off template from a one-off table. A one-off template allows the client to create a new recipient of a particular type. Most of the fields are editable. The template pointed to by the  _lpEntryID_ parameter might be one that your provider supplies or it might be a template from a foreign provider, if your provider supports foreign templates. Implementations of **CreateEntry** for providers that can create recipients from a foreign template are always more complex than implementations for providers that cannot. 
  
 **To implement IABContainer::CreateEntry**
  
1. Determine the type of entry identifier specified by the  _lpEntryID_ parameter. 
    
2. If the entry identifier represents a template for a messaging user, distribution list, or address book container owned by your provider:
    
1. Create and initialize the appropriate object. Your provider can set some initial properties if desired. These properties depend on the type of recipient being created. 
    
2. Return a pointer to the object's implementation in the contents of the  _lppMAPIPropEntry_ parameter. 
    
3. If the entry identifier represents a template for a foreign provider:
    
1. Call [IMAPISupport::OpenEntry](imapisupport-openentry.md) to open the foreign object. 
    
2. Call the object's [IMAPIProp::GetProps](imapiprop-getprops.md) method, passing NULL for the property tag array, to retrieve its properties. 
    
3. Edit the property value array returned from **GetProps** by changing the property tag to PR_NULL for all properties that will not apply to the new object and should not be transferred. 
    
4. Create an entry identifier for the new object. 
    
5. Create a new object of the appropriate type, either messaging user or distribution list.
    
6. Initialize the new object by setting default properties.
    
7. Check whether or not the foreign object supports the **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property. 
    
8. If the foreign object supports **PR_TEMPLATEID**, call [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md) to retrieve a property object interface from the foreign provider and set the contents of the  _lppMAPIPropEntry_ parameter to the foreign property object implementation. 
    
9. If the foreign object does not support **PR_TEMPLATEID**, set the contents of the  _lppMAPIPropEntry_ parameter to your provider's implementation of the new object. 
    
10. Call the [IMAPIProp::SetProps](imapiprop-setprops.md) method of the object pointed to by the  _lppMAPIPropEntry_ parameter to set the appropriate properties from the foreign object. 
    

