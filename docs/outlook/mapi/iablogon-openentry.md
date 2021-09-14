---
title: "IABLogonOpenEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IABLogon.OpenEntry
api_type:
- COM
ms.assetid: 1cfb82f7-5215-4faa-af25-5b1da7e31209
description: "Last modified: July 23, 2011"
---

# IABLogon::OpenEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a container, messaging user, or distribution list, and returns a pointer to an interface implementation to provide further access.
  
```cpp
HRESULT OpenEntry(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  ULONG ulFlags,
  ULONG FAR * lpulObjType,
  LPUNKNOWN FAR * lppUnk
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the container, messaging user, or distribution list to open.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the open object. Passing NULL returns the identifier for the object's standard interface. For containers, the standard interface is [IABContainer : IMAPIContainer](iabcontainerimapicontainer.md). The standard interfaces for address book objects are [IDistList : IMAPIContainer](idistlistimapicontainer.md) for a distribution list and [IMailUser : IMAPIProp](imailuserimapiprop.md) for a messaging user. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the object is opened. The following flags can be set:
    
MAPI_BEST_ACCESS 
  
> Requests that the object be opened with the maximum network permissions allowed for the user and the maximum client application access. For example, if the client has read/write permission, the object should be opened with read/write permission; if the client has read-only permission, the object should be opened with read-only permission.
    
MAPI_DEFERRED_ERRORS 
  
> Allows the **OpenEntry** method to return successfully, possibly before the calling client has fully accessed the object. If the object is not accessed, making a subsequent object call can raise an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened with read-only access, and clients should not assume that read/write permission has been granted.
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppUnk_
  
> [out] A pointer to a pointer to the opened object.
    
## Remarks

S_OK 
  
> The object was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> Either the user has insufficient permissions to open the object, or an attempt was made to open a read-only object with read/write permission.
    
MAPI_E_NOT_FOUND 
  
> The entry identifier specified by  _lpEntryID_ does not represent an object. 
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The entry identifier in the  _lpEntryID_ parameter is not of a format recognized by the address book provider. 
    
## Remarks

MAPI calls the **OpenEntry** method to open a container, messaging user, or distribution list. 
  
## Notes to implementers

Before MAPI calls your **OpenEntry** method, it determines that the entry identifier in the  _lpEntryID_ parameter belongs to you and not to another provider. MAPI does this by matching the [MAPIUID](mapiuid.md) structure in the entry identifier with the **MAPIUID** that you registered by calling the [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) method at startup. 
  
Open the object as read-only, unless the MAPI_MODIFY or MAPI_BEST_ACCESS flag is set in the  _ulFlags_ parameter. If you do not allow modification for the requested object, do not open the object at all and return MAPI_E_NO_ACCESS. 
  
If MAPI passes NULL for  _lpEntryID_, open the root container in your container hierarchy.
  
The object that you are being asked to open might be an object copied from another provider. In this case, it will support the **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property. If the object does support this property, call the [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md) method to bind to code for this entry in the foreign provider, passing **PR_TEMPLATEID** in the  _lpTemplateID_ parameter and 0 in the  _ulTemplateFlags_ parameter. **IMAPISupport::OpenTemplateID** passes this information to the foreign provider in a call to the foreign provider's [IABLogon::OpenTemplateID](iablogon-opentemplateid.md) method. If **IMAPISupport::OpenTemplateID** raises an error, usually because the foreign provider is unavailable or not included in the profile, try to continue by treating the unbound entry as read-only. For more information about opening foreign address book entries, see [Acting as a Host Address Book Provider](acting-as-a-host-address-book-provider.md).
  
## See also



[IABLogon : IUnknown](iablogoniunknown.md)

