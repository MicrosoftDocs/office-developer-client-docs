---
title: "Acting as a Foreign Address Book Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 6d532ed4-7dc5-46a9-995a-72bc97d16f6e
description: "Last modified: July 23, 2011"
 
 
---

# Acting as a Foreign Address Book Provider

  
  
**Applies to**: Outlook 
  
A foreign provider is an address book provider that: 
  
- Assigns template identifiers for its recipients.
    
- Supports the [IABLogon::OpenTemplateID](iablogon-opentemplateid.md) method. 
    
- Supplies code for maintaining recipients that exist in the containers of other address book providers known as host providers. This code involves a property object, typically an **IMAPIProp** interface implementation, which wraps a property object from the host provider. 
    
Acting as a foreign provider is an optional role; not all providers need to support template identifiers and their related code. Implement your provider as a foreign provider if you want to maintain control over recipients that host providers create using templates supplied by your provider. 
  
The format that your provider uses for its entry identifiers can also be used for its template identifiers. Template identifiers must include your provider's registered **MAPIUID** to enable MAPI to successfully bind recipients to the appropriate providers. 
  
MAPI calls your provider's **IABLogon::OpenTemplateID** method when a host provider calls [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md). The host provider passes the template identifier of the recipient in the  _lpTemplateID_ parameter in its call to **IMAPISupport::OpenTemplateID**. MAPI determines that the template identifier belongs to your provider by matching the [MAPIUID](mapiuid.md) in the template identifier with the **MAPIUID** that your provider registered at logon time. MAPI then forwards the host provider's call to your provider through the **IABLogon::OpenTemplateID** method. 
  
The host provider also passes a pointer to its property object implementation for the recipient in the  _lpMAPIPropData_ parameter, an interface identifier in the  _lpInterface_ parameter that corresponds to the type of interface implementation passed in  _lpMAPIPropData_, and an optional flag, FILL_ENTRY. Your provider is expected to return in the  _lppMAPIPropNew_ parameter a pointer to a property object implementation of the type specified in  _lpInterface_. The returned pointer can either be to the wrapped property object implemented by your provider or to the object supplied by the host provider in  _lpMAPIPropData_. Your provider should return a wrapped property object pointer when:
  
- The recipient's display table contains list box controls.
    
- The e-mail address for the recipient must be assembled from data in multiple display table controls.
    
- Your provider issues display table notifications.
    
The FILL_ENTRY flag indicates to your provider that the host provider requires all the properties of the recipient to be updated. Your provider is required to fulfill this request.
  
When a host provider calls your provider's **OpenTemplateID** method, your provider might: 
  
- Periodically update the data for a copied entry.
    
- Keep a copied entry synchronized with its original, such as when an address book entry is copied to the personal address book.
    
- Implement functionality that cannot be implemented by the host provider, such as dynamically populating list boxes in the copied entry's details table from data on a server.
    
- Control the interaction among properties in a copied entry or instantiated template. For example, computing **PR_EMAIL_ADDRESS** from other properties displayed in the details table. 
    
The first two items are examples of tasks that do not require your provider to supply a wrapped property object — an implementation of **IMAPIProp** that is based on the host provider's implementation. Your provider can simply update the properties as necessary and return, setting the  _lppMAPIPropNew_ parameter to point to the pointer passed in by the host provider in the  _lpMAPIPropData_ parameter. 
  
The second two tasks require that your provider return to the host provider a property object that wraps the host provider's object with additional functionality, such as the ability to display a property sheet for the entry. This property object will either be a messaging user or distribution list, depending on the type of object passed in by the host provider in the  _lpMAPIPropData_ parameter and indicated by the interface identifier in the  _lpInterface_ parameter. If the  _lpMAPIPropData_ parameter points to a messaging user, your provider's wrapped property object must be an **IMailUser** implementation. If  _lpMAPIPropData_ points to a distribution list, it must be an **IDistList** implementation. 
  
Your provider's wrapped property object intercepts **IMAPIProp** method calls to perform context-specific manipulation of the host provider's recipient — the object it is wrapping. MAPI only has one requirement for wrapped property objects: all calls to [IMAPIProp::OpenProperty](imapiprop-openproperty.md) requesting the **PR_DETAILS_TABLE** ( [PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property should be passed to the host provider. Your provider's implementation can use the returned table to intercept display table notifications or to add its own if necessary. 
  
The following list includes tasks that are typically implemented in the wrapped property object implemented by foreign providers:
  
- Preprocessing and postprocessing property values for the host recipient in [IMAPIProp::GetProps](imapiprop-getprops.md).
    
- Handling details display table controls, such as buttons and list boxes, in **IMAPIProp::OpenProperty**.
    
- Validating or manipulating property values for the host recipient in [IMAPIProp::SetProps](imapiprop-setprops.md).
    
- Computing required properties such as **PR_EMAIL_ADDRESS** and verifying that all of the necessary properties have been set before saving the host recipient in [IMAPIProp::SaveChanges](imapiprop-savechanges.md).
    
 **To implement IABLogon::OpenTemplateID**
  
1. Check if the template identifier passed in with the  _lpTemplateID_ parameter is valid and is in a format that your provider recognizes. If it is not, fail and return MAPI_E_INVALID_ENTRYID. 
    
2. Create an object of the type indicated by the template identifier, either a messaging user, distribution list, or one-off recipient. 
    
3. Call the **IUnknown::AddRef** method in the host provider's property object, which is the object pointed to by the  _lpMAPIPropData_ parameter. 
    
4. If the  _ulTemplateFlags_ parameter is set to FILL_ENTRY: 
    
1. If the new object is a messaging user or distribution list:
    
1. Retrieve all of the properties of the new object, possibly by calling its **IMAPIProp::GetProps** method. 
    
2. Call the host provider's **IMAPIProp::SetProps** method to copy all of the retrieved properties to the host provider's property object. 
    
2. If the new object is a one-off recipient, call the host provider's **IMAPIProp::SetProps** method to set the following properties: 
    
  - **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md)) to the address type handled by your provider.
    
  - **PR_TEMPLATEID** ( [PidTagTemplateid](pidtagtemplateid-canonical-property.md)) to the template identifier from the  _lpTemplateID_ and  _cbTemplateID_ parameters. 
    
  - **PR_DISPLAY_TYPE** ( [PidTagDisplayType](pidtagdisplaytype-canonical-property.md)) to DT_MAILUSER or DT_DISTLIST, as appropriate.
    
5. Set the contents of the  _lppMAPIPropNew_ parameter to point to either your provider's new object or the property object passed in with the  _lpMAPIPropData_ parameter, depending on whether your provider determines a wrapped object is necessary. 
    
6. If a critical error occurs, such as a network failure or an out of memory condition, return the appropriate error value. This value should get propagated to the client with the appropriate [MAPIERROR](mapierror.md) structure, a task performed by the host provider. 
    

