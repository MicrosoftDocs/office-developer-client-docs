---
title: "IAddrBookCompareEntryIDs"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBookCompareEntryIDs
api_type:
- COM
ms.assetid: 7dabc1d3-5ea4-482f-91a9-9ef3009eddd2
description: "Last modified: July 23, 2011"
---

# IAddrBook::CompareEntryIDs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two entry identifiers that belong to a particular address book provider to determine whether they refer to the same address book object. 
  
```cpp
HRESULT CompareEntryIDs(
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
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID1_ parameter. 
    
 _lpEntryID1_
  
> [in] A pointer to the first entry identifier to be compared.
    
 _cbEntryID2_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID2_ parameter. 
    
 _lpEntryID2_
  
> [in] A pointer to the second entry identifier to be compared.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpulResult_
  
> [out] A pointer to the result of the comparison. The contents of  _lpulResult_ are set to TRUE if the two entry identifiers refer to the same object; otherwise, the contents are set to FALSE. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_UNKNOWN_ENTRYID 
  
> One or both of the entry identifiers passed in with the  _lpEntryID1_ or  _lpEntryID2_ parameters are not recognized by any address book provider. 
    
## Remarks

Client applications and service providers call the **CompareEntryIDs** method to compare two entry identifiers that belongs to a single address book provider to determine whether they refer to the same object. **CompareEntryIDs** is useful because an object can have more than one valid entry identifier. This situation can occur, for example, after a new version of an address book provider is installed. 
  
MAPI passes this call to the address book provider that is responsible for the entry identifiers, determining the appropriate provider by matching the [MAPIUID](mapiuid.md) structure in the entry identifiers with the **MAPIUID** structure registered by the provider. 
  
If the two entry identifiers refer to the same object, **CompareEntryIDs** sets the contents of the  _lpulResult_ parameter to TRUE; if they refer to different objects, **CompareEntryIDs** sets the contents to FALSE. In either case, **CompareEntryIDs** returns S_OK. If **CompareEntryIDs** returns an error, which can occur if no address book provider has registered a **MAPIUID** structure that matches the one in the entry identifiers, clients and providers should not take any action based on the result of the comparison. They should instead take the most conservative approach to the action being performed. 
  
## See also



[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

