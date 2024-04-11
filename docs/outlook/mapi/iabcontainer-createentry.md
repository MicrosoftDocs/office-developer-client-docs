---
title: "IABContainerCreateEntry"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IABContainer.CreateEntry
api_type:
- COM
ms.assetid: ea1daf74-d9e3-4304-bf5d-889afeea6ae9
---

# IABContainer::CreateEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a new entry, which can be a messaging user, a distribution list, or another container.
  
```cpp
HRESULT CreateEntry(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulCreateFlags,
  LPMAPIPROP FAR * lppMAPIPropEntry
);
```

## Parameters

 _cbEntryID_
  
> [in] The count of the bytes in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of a template for creating new entries of a particular type. 
    
 _ulCreateFlags_
  
> [in] A bitmask of flags that controls how entry creation is performed. The following flags can be set:
    
CREATE_CHECK_DUP_LOOSE 
  
> A loose level of duplicate entry checking should be performed. The implementation of loose duplicate entry checking is provider specific. For example, a provider can define a loose match as any two entries that have the same display name.
    
CREATE_CHECK_DUP_STRICT 
  
> A strict level of duplicate entry checking should be performed. The implementation of strict duplicate entry checking is provider specific. For example, a provider can define a strict match as any two entries that have both the same display name and messaging address.
    
CREATE_REPLACE 
  
> A new entry should replace an existing one if it is determined that the two are duplicates.
    
 _lppMAPIPropEntry_
  
> [out] A pointer to a pointer to the newly created entry.
    
## Return value

S_OK 
  
> The new entry was successfully created.
    
## Remarks

The **IABContainer::CreateEntry** method creates a new entry of a particular type in the specified container, returning a pointer to an interface implementation for further access to the entry. The new entry is created by using a template that has been selected from the container's list of available templates published in its one-off table. Callers access a container's one-off table by calling its [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method and requesting the **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property. 
  
## Notes to implementers

All containers that support the **IABContainer::CreateEntry** method must be modifiable. Set your container's AB_MODIFIABLE flag in its **PR_CONTAINER_FLAGS** ([PidTagContainerFlags](pidtagcontainerflags-canonical-property.md)) property to indicate that it is modifiable. 
  
You should support all of the  _ulCreateFlags_ flags. However, the interpretation and use of these flags is implementation specific—that is, you can determine what the semantics of CREATE_CHECK_DUP_LOOSE and CREATE_CHECK_DUP_STRICT mean in the context of your implementation. If you cannot or do not determine whether an entry is a duplicate, always allow the entry to be created. 
  
Some providers implement strict entry checking by matching the display name, messaging address, and search key in an entry; other providers limit the match to display name and address. Loose entry checking is often implemented by checking the display name only. 
  
## Notes to Host Address Book Provider Implementers

If your container can create entries from the templates of other providers, your implementation of **CreateEntry** should provide storage for some or all of the properties associated with the created entries. For example, if you provide storage for an entry's **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property, you can generate its details dialog box without having to depend on the foreign provider. 
  
If your container can create entries that support the **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property, your implementation of **CreateEntry** must do the following: 
  
1. Call the [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md) method. **OpenTemplateID** enables the foreign provider's code for the entry to bind to the new entry being created. Foreign providers support this binding process to maintain control over entries created from their templates into the containers of host address book providers. 
    
2. Perform any necessary initialization, and populate the new object with all of the properties from the entry in the foreign provider that the object returned in the _lppMAPIPropNew_ parameter from **OpenTemplateID**.
    
If **OpenTemplateID** succeeds, copy the properties to the implementation pointed to by the  _lppMAPIPropNew_ parameter rather than directly to the implementation pointed to by the  _lpMAPIPropData_ parameter. Initialize the new entry for offline use as you would any other entry from a foreign provider. 
  
If **OpenTemplateID** returns an error, **CreateEntry** should fail. Do not allow the entry to be created. Because the foreign provider can make assumptions about the data in your provider, do not create an entry with a template identifier that has not been successfully bound to the foreign provider. 
  
## Notes to callers

When **CreateEntry** returns, you may or may not be able to immediately access the entry identifier for the new entry. Some address book providers do not make it available until after you have called the new entry's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. 
  
Although duplicate checking flags are passed as parameters to **CreateEntry**, the duplicate checking operation does not occur until **SaveChanges** is called. Therefore, related errors such as MAPI_E_COLLISION, which indicates that an attempt was made to create an already existing entry, are returned by **SaveChanges** rather than **CreateEntry**.
  
## See also



[IABContainer::CopyEntries](iabcontainer-copyentries.md)
  
[IMAPIProp::OpenProperty](imapiprop-openproperty.md)
  
[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[PidTagCreateTemplates Canonical Property](pidtagcreatetemplates-canonical-property.md)
  
[IABContainer : IMAPIContainer](iabcontainerimapicontainer.md)

