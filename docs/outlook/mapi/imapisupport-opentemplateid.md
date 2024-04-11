---
title: "IMAPISupportOpenTemplateID"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.OpenTemplateID
api_type:
- COM
ms.assetid: 532f7af0-b2cc-49dd-b1de-e3ec1dc9a3e7
---

# IMAPISupport::OpenTemplateID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a recipient entry in a foreign address book provider.
  
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
  
> [in] The byte count in the template identifier pointed to by  _lpTemplateID_. 
    
 _lpTemplateID_
  
> [in] A pointer to the template identifier **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property of the recipient entry to be opened.
    
 _ulTemplateFlags_
  
> [in] A bitmask of flags used to describe how to open the entry. The following flag can be set:
    
FILL_ENTRY 
  
> A new entry is being created. When the foreign provider receives the subsequent [IABLogon::OpenTemplateID](iablogon-opentemplateid.md) call from MAPI, it can control how the entry is created by modifying properties pointed to by the  _lpMAPIPropData_ parameter or by returning a specific interface implementation in  _lppMAPIPropNew_ to control how properties for the new entry are set. 
    
 _lpMAPIPropData_
  
> [in] A pointer to the interface implementation that the caller uses to access the entry. This is the implementation that the foreign provider can wrap with its own implementation and return in the _lppMAPIPropNew_ parameter. The  _lpMAPIPropData_ parameter must point to a read/write interface implementation that derives from [IMAPIProp : IUnknown](imapipropiunknown.md) and supports the interface being requested in the _lpInterface_ parameter. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the entry. The  _lppMAPIPropNew_ parameter points to an interface of the type specified by  _lpInterface_. Passing NULL returns the standard interface for a messaging user, IID_IMailUser. 
    
 _lppMAPIPropNew_
  
> [out] A pointer to the interface implementation that the foreign provider supplies for accessing the entry.
    
 _lpMAPIPropSibling_
  
> Reserved; must be NULL.
    
## Return value

S_OK 
  
> The binding process was successful.
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The foreign address book provider doesn't exist.
    
## Remarks

The **IMAPISupport::OpenTemplateID** method is implemented only for address book provider support objects. **OpenTemplateID** is called only by address book providers that can act as hosts for entries that belong to other address book providers, also known as foreign providers. Host providers call **OpenTemplateID** to open a foreign entry, which occurs when data in the host provider is bound to code in the foreign provider. 
  
## Notes to callers

Call **OpenTemplateID** only if you support the storage of entries with template identifiers from foreign address book providers. Such support places additional requirements on your [IABContainer::CreateEntry](iabcontainer-createentry.md) and [IABLogon::OpenEntry](iablogon-openentry.md) implementations. For more information, see the descriptions of these methods and [Acting as a Host Address Book Provider](acting-as-a-host-address-book-provider.md).
  
If the **OpenTemplateID** call returns as the bound interface the same property object implementation that you passed in, you can release your reference to your property object. This is because the foreign provider has called the object's **AddRef** method to keep its own reference. If the foreign provider does not need to keep a reference to the property object, then **OpenTemplateID** will return the unbound property object. 
  
If **OpenTemplateID** fails with MAPI_E_UNKNOWN_ENTRYID, try to continue by treating the entry as read-only. 
  
## See also



[IABLogon::OpenTemplateID](iablogon-opentemplateid.md)
  
[IPropData : IMAPIProp](ipropdataimapiprop.md)
  
[PidTagTemplateid Canonical Property](pidtagtemplateid-canonical-property.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

