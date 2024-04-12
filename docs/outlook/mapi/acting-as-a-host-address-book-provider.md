---
title: "Acting as a Host Address Book Provider"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: f06a1034-ee49-4a09-831e-9752713228a8
 
---

# Acting as a Host Address Book Provider

**Applies to**: Outlook 2013 | Outlook 2016
  
A host provider is an address book provider that includes recipients from other providers in its containers and relies on the implementation of the recipients by the other providers to partially control their maintenance. A host provider uses the template identifiers of these foreign recipients to bind the data for these recipients to code in the foreign provider. This binding process is initiated when your provider retrieves the **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property of a recipient and passes it in a call to [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md).
  
When your provider calls **IMAPISupport::OpenTemplateID**, MAPI matches the **MAPIUID** within the template identifier with a **MAPIUID** registered by a provider and calls the provider's [IABLogon::OpenTemplateID](iablogon-opentemplateid.md) method. The foreign provider might return a pointer to your provider's property object, to its own property object implementation, or to an implementation that wraps your provider's object. The returned pointer is placed in the contents of the _lppMAPIPropNew_ parameter.
  
Your provider can choose whether or not to call **IMAPISupport::OpenTemplateID** with the FILL_ENTRY flag set. Set this flag when the recipient is being created or when a long time has passed since your provider has refreshed the recipient's properties. A common use of the FILL_ENTRY flag is to keep a recipient in your provider synchronized with the original. Implementing this type of synchronization schedule enhances performance.
  
 **To keep a foreign recipient synchronized**
  
1. Determine an appropriate interval for periodic updates.

2. Timestamp each call to [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md).

3. Evaluate whether or not it is necessary to perform a full update based on the amount of time that has expired since the last call. If a full update is necessary, call **IMAPISupport::OpenTemplateID** with the FILL_ENTRY flag. If it is not necessary, do not set the flag on the call.

When a client makes a request for one of the copied recipient's properties, your provider can choose whether to handle the request itself or use the code supplied by the foreign provider. Your provider can expect the foreign provider to intercept most, if not all, calls to **IMAPIProp** except for [IMAPIProp::OpenProperty](imapiprop-openproperty.md). A call to **OpenProperty** requesting the **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property is always forwarded to your provider.
  
 **To access template identifier code**
  
1. Open the recipient and call its [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property. If **GetProps** fails because **PR_TEMPLATEID** is unavailable, the foreign provider does not support a template identifier and related code for this recipient. Your provider will need to use its implementation of the recipient for all maintenance.

2. If the template identifier is returned from **GetProps**, pass it and a pointer to the recipient's **IMAPIProp** implementation in a call to the **IMAPISupport::OpenTemplateID** method. Set the FILL_ENTRY flag if most or all of the recipient's properties need to be updated, such as at creation time or if they have not been updated for a while.

3. If **OpenTemplateID** returns the foreign provider's **IMAPIProp** implementation, return to the client a pointer to this implementation.

4. If **OpenTemplateID** does not return an implementation, typically because the foreign provider is not in the profile, return to the client a pointer to your provider's **IMAPIProp** implementation. The client should be able to work with the object's properties using either interface.
