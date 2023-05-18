---
title: "IMSProviderCompareStoreIDs"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMSProvider.CompareStoreIDs
api_type:
- COM
ms.assetid: c3e3cfaa-9c4a-482a-9411-9c4ab01d312f
---

# IMSProvider::CompareStoreIDs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two message store entry identifiers to determine whether they refer to the same store object.
  
```cpp
HRESULT CompareStoreIDs(
  ULONG cbEntryID1,
  LPENTRYID lpEntryID1,
  ULONG cbEntryID2,
  LPENTRYID lpEntryID2,
  ULONG ulFlags,
  ULONG FAR * lpulResult
);
```

## Parameters

 _cbEntryID1_
  
> [in] The size, in bytes, of the entry identifier pointed to by the  _lpEntryID1_ parameter  _._
    
 _lpEntryID1_
  
> [in] A pointer to the first entry identifier to be compared.
    
 _cbEntryID2_
  
> [in] The size, in bytes, of the entry identifier pointed to by the  _lpEntryID2_ parameter  _._
    
 _lpEntryID2_
  
> [in] A pointer to the second entry identifier to be compared.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpulResult_
  
> [out] A pointer to the returned result of the comparison. TRUE if the two entry identifiers refer to the same object; otherwise, FALSE.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

MAPI calls the **IMSProvider::CompareStoreIDs** method when it processes a call to the [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) method. **CompareStoreIDs** is called at this point to determine which profile section, if any, is associated with the message store being opened. A **CompareStoreIDs** call can be made when no message stores are open for a particular store provider. In addition, MAPI also calls **CompareStoreIDs** when it processes a store provider call to the [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) method. 
  
The entry identifiers compared by **CompareStoreIDs** are both for the current store provider's dynamic-link library (DLL) and are both unwrapped store entry identifiers. For more information about wrapping store entry identifiers, see [IMAPISupport::WrapStoreEntryID](imapisupport-wrapstoreentryid.md).
  
Comparing entry identifiers is useful because an object can have more than one valid entry identifier. This can occur, for example, after a new version of a message store provider is installed. 
  
## See also



[IMAPISession::OpenMsgStore](imapisession-openmsgstore.md)
  
[IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md)
  
[IMAPISupport::WrapStoreEntryID](imapisupport-wrapstoreentryid.md)
  
[IMSProvider : IUnknown](imsprovideriunknown.md)

