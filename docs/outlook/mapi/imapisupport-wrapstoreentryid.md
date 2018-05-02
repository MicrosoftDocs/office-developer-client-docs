---
title: "IMAPISupportWrapStoreEntryID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.WrapStoreEntryID
api_type:
- COM
ms.assetid: 923fb879-5f32-4fe2-8920-2ec17002256c
description: "Last modified: July 23, 2011"
---

# IMAPISupport::WrapStoreEntryID

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Converts a message store's internal entry identifier to an entry identifier in the MAPI standard format.
  
```
HRESULT WrapStoreEntryID(
ULONG cbOrigEntry,
LPENTRYID lpOrigEntry,
ULONG FAR * lpcbWrappedEntry,
LPENTRYID FAR * lppWrappedEntry
);
```

## Parameters

 _cbOrigEntry_
  
> [in] The byte count in the entry identifier pointed to by the  _lpOrigEntry_ parameter. 
    
 _lpOrigEntry_
  
> [in] A pointer to the private entry identifier for the message store.
    
 _lpcbWrappedEntry_
  
> [out] A pointer to the byte count in the entry identifier pointed to by the  _lppWrappedEntry_ parameter. 
    
 _lppWrappedEntry_
  
> [out] A pointer to a pointer to the wrapped entry identifier.
    
## Return value

S_OK 
  
> The entry identifier was successfully wrapped.
    
## Remarks

The **IMAPISupport::WrapStoreEntryID** method is implemented for all service provider support objects. Service providers use **WrapStoreEntryID** to have MAPI generate an entry identifier for a message store that wraps the store's internal entry identifier. 
  
## Notes to Callers

When a client calls your message store's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve its **PR_STORE_ENTRYID** ( [PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md)) property, and your message store uses an entry identifier in a private format, call **WrapStoreEntryID** and return the entry identifier pointed to by the  _lppWrappedEntry_ parameter. 
  
Calls to the [IMSProvider::Logon](imsprovider-logon.md) and [IMSLogon::CompareEntryIDs](imslogon-compareentryids.md) methods always obtain the store's private entry identifier; the wrapped version is used only between client applications and MAPI. 
  
Free the memory for the entry identifier pointed to by the  _lppWrappedEntry_ parameter by using the [MAPIFreeBuffer](mapifreebuffer.md) function when you are finished using the entry identifier. 
  
## See also

#### Reference

[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPISupport::CompareEntryIDs](imapisupport-compareentryids.md)
  
[IMSLogon::CompareEntryIDs](imslogon-compareentryids.md)
  
[IMSProvider::Logon](imsprovider-logon.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

