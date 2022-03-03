---
title: "IABLogonOpenTemplateID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IABLogon.OpenTemplateID
api_type:
- COM
ms.assetid: 751c36d3-c39e-4357-a60a-88685a378de0
---

# IABLogon::OpenTemplateID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a recipient entry that has data residing in a host address book provider.
  
```cpp
HRESULT OpenTemplateID(
  ULONG cbTemplateID,
  LPENTRYID lpTemplateID,
  ULONG ulTemplateFlags,
  LPMAPIPROP lpMAPIPropData,
  LPCIID lpInterface,
  LPMAPIPROP FAR * lppMAPIPropNew,
  LPMAPIPROP lpMAPIPropSibling
);
```

## Parameters

 _cbTemplateID_
  
> [in] The byte count in the template identifier pointed to by the  _lpTemplateID_ parameter. 
    
 _lpTemplateID_
  
> [in] A pointer to the template identifier, or **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property, of the recipient entry to be opened.
    
 _ulTemplateFlags_
  
> [in] A bitmask of flags used to indicate how to open the entry represented by the template identifier. The following flag can be set:
    
FILL_ENTRY 
  
> The host provider is creating a new entry in its container based on the entry represented by the template identifier. The **IABLogon::OpenTemplateID** method should either perform specific initialization of the host provider's entry by using the [IMAPIProp : IUnknown](imapipropiunknown.md) implementation in the _lpMAPIPropData_ parameter, or return a custom **IMAPIProp** interface implementation in the _lppMAPIPropNew_ parameter. 
    
 _lpMAPIPropData_
  
> [in] A pointer to the host provider's property object and implementation of an interface derived from **IMAPIProp**.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the type of interface pointer to be returned in the _lppMAPIPropNew_ parameter. Passing **null** returns the standard messaging user interface, [IMailUser : IMAPIProp](imailuserimapiprop.md).
    
 _lppMAPIPropNew_
  
> [out] A pointer to the bound property object and an implementation of an interface derived from **IMAPIProp**.
    
 _lpMAPIPropSibling_
  
> [out] Reserved; must be **null**.
    
## Return value

S_OK 
  
> The appropriate code was successfully bound to related data in the host provider.
    
MAPI_E_NO_SUPPORT 
  
> The object does not support template IDs.
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The template identifier passed in the _lpTemplateID_ parameter is not recognized by the address book provider. 
    
## Remarks

The **IABLogon::OpenTemplateID** method is implemented only by address book providers that need to maintain control over copies of their entries that are located in the containers of host providers. Providers that implement **OpenTemplateID** are known as foreign address book providers. Host providers call [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md) to create a copied entry or open the copied entry, and MAPI passes on the call to **IABLogon::OpenTemplateID**. **IABLogon::OpenTemplateID** opens the entry and binds the code that controls it to data in the host provider. 
  
Rather than use an entry identifier, **IABLogon::OpenTemplateID** uses another property, the entry's template identifier, **PR_TEMPLATEID**. Template identifiers should be supported for entries whose code must be bound to data in a host provider.
  
Some examples of when an address book provider should implement **IABLogon::OpenTemplateID** are as follows: 
  
- To periodically update the data for a copied entry so that it stays synchronized with the original.
    
- To implement functionality that the host provider cannot implement, such as dynamically populating a list that appears in the entry's details table from data on a server.
    
- To control the interaction between properties in the host provider's entry and the original entry, such as computing the **PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) from the values of the edit controls in the details display that contain different components of the address.
    
## Notes to implementers

When a host provider copies or creates an entry from your provider and you supply a property object implementation through **IABLogon::OpenTemplateID**, you handle most of the calls to maintain the entry. However, because it is up to the host provider to forward these calls to you, the host provider can intercept any call and perform custom processing before forwarding the call.
  
You should use the following guidelines in your property object implementations:
  
- When [IMAPIProp::GetProps](imapiprop-getprops.md) is called, determine whether the request is for a computed property and, if it is, handle it. Transfer all requests for noncomputed properties to the host provider. 
    
- When [IMAPIProp::OpenProperty](imapiprop-openproperty.md) is called to open any table except the details display table, handle the request. Most tables cannot be copied accurately to the host provider. You must generate the **IMAPITable** implementation for these requested tables. The details table **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property must be copied to the host provider. This allows this provider to generate the table locally. You might want to wrap the display table implementation to generate display table notifications. 
    
- When [IMAPIProp::SetProps](imapiprop-setprops.md) is called, the host provider can validate the data before letting you set the properties. You can verify that all of the necessary properties were set or computed. If an error is detected, return the appropriate error value and, if you can, any additional explanation through [IMAPIProp::GetLastError](imapiprop-getlasterror.md).
    
- When [IMAPIProp::SaveChanges](imapiprop-savechanges.md) is called, the host provider might want to perform processing before you save the entry. You should save any data that is affected by the changed properties, such as a new address, in the host provider's entry. 
    
In general, make your implementation of the entry that you pass back to the host provider intercept all of the methods to perform context-specific manipulation of the relevant properties. If the FILL_ENTRY flag is passed in the _ulTemplateFlags_ parameter, set all properties for the entry. 
  
If you return a new property object in the _lppMAPIPropNew_ parameter, call the [IUnknown::AddRef](https://msdn.microsoft.com/library/ms691379%28VS.85%29.aspx) method of the host provider's property object to maintain a reference. All calls through the bound object that the **IMAPIProp** implementation returned in  _lppMAPIPropNew_ should be routed to their corresponding method in the host property object after they are dealt with by the bound object. 
  
The property identifiers of any named properties that are passed through your bound property object are in your provider's identifier namespace. Your implementation of the [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) method should determine the names of the properties so that it can perform any template-specific tasks. Similarly, properties that your provider passes on to the host provider must also be in your namespace. For example, if you set a named property in **OpenTemplateID**, you should use one of your identifiers for the name—creating it, if necessary, by calling the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) method. 
  
If you do not recognize the entry identifier passed in  _lpTemplateID_, return MAPI_E_UNKNOWN_ENTRYID.
  
For more information about how to work with address book template identifiers, see [Acting as a Foreign Address Book Provider](acting-as-a-foreign-address-book-provider.md).
  
## See also



[IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md)
  
[IPropData : IMAPIProp](ipropdataimapiprop.md)
  
[PidTagTemplateid Canonical Property](pidtagtemplateid-canonical-property.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)

