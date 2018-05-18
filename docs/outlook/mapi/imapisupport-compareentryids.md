---
title: "IMAPISupportCompareEntryIDs"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.CompareEntryIDs
api_type:
- COM
ms.assetid: be6991d9-6353-4838-bc6b-39de51a94d8d
description: "Last modified: July 23, 2011"
---

# IMAPISupport::CompareEntryIDs

  
  
**Applies to**: Outlook 
  
Compares two entry identifiers to determine whether they refer to the same object. 
  
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
  
> [out] A pointer to the result of the comparison. TRUE if the two entry identifiers refer to the same object; otherwise, FALSE.
    
## Return value

S_OK 
  
> The comparison was successful.
    
MAPI_E_UNKNOWN_ENTRYID 
  
> One or both of the entry identifiers specified as parameters do not refer to valid objects, possibly because they are currently unopened and unavailable.
    
## Remarks

The **IMAPISupport::CompareEntryIDs** method is implemented for address book and message store provider support objects. **CompareEntryIDs** compares two entry identifiers that belong to a single service provider to determine whether they refer to the same object. MAPI extracts the [MAPIUID](mapiuid.md) portion from the entry identifiers to determine the service provider responsible for the objects. MAPI then calls its logon object's **CompareEntryIDs** method to perform the comparison. 
  
## Notes to Callers

 **CompareEntryIDs** is useful because an object can have more than one valid entry identifier. This situation can occur, for example, after a new version of a service provider is installed. 
  
If **CompareEntryIDs** returns an error, do not take any action based on the result of the comparison. Instead, take the most conservative approach possible. **CompareEntryIDs** might fail if, for example, one or both of the entry identifiers contain an invalid **MAPIUID** structure. 
  
## See also

#### Reference

[MAPIUID](mapiuid.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

