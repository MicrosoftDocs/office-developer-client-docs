---
title: "IABLogonCompareEntryIDs"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IABLogon.CompareEntryIDs
api_type:
- COM
ms.assetid: cb4a38ff-2fdd-40ac-a613-12c3f11a1df9
---

# IABLogon::CompareEntryIDs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two entry identifiers to determine whether they refer to the same object.
  
```cpp
HRESULT CompareEntryIDs(
  ULONG cbEntryID1,
  LPENTRYID lpEntryID1,
  ULONG cbEntryID2,
  LPENTRYID lpEntryID2,
  ULONG ulFlags,
  ULONG FAR * lpulRet
);
```

## Parameters

 _cbEntryID1_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID1_ parameter. 
    
 _lpEntryID1_
  
> [in] A pointer to the first entry identifier to be compared.
    
 _cbEntryID2_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID2_ parameter. 
    
 _lpEntryID2_
  
> [in] A pointer to the second entry identifier to be compared.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpulRet_
  
> [out] A pointer to the result of the comparison. TRUE to indicate that the two entry identifiers refer to the same object; otherwise, FALSE.
    
## Return value

S_OK 
  
> The entry identifiers were successfully compared.
    
MAPI_E_INVALID_ENTRYID 
  
> One or both of the entry identifiers do not belong to the address book provider.
    
## Remarks

Address book providers implement the **CompareEntryIDs** method to compare two entry identifiers to determine whether they refer to the same object. 
  
 **CompareEntryIDs** is useful because an object can have more than one valid entry identifier; such a situation can occur, for example, when you compare a short-term entry identifier with a long-term entry identifier. 
  
For more information about how to create entry identifiers, see [MAPI Entry Identifiers](mapi-entry-identifiers.md).
  
## See also



[IABLogon : IUnknown](iablogoniunknown.md)

