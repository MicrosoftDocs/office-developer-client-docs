---
title: "IMAPISessionCompareEntryIDs"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.CompareEntryIDs
api_type:
- COM
ms.assetid: 319f10e9-db8d-4d16-aa1f-6cf5fef493eb
description: "Last modified: March 09, 2015"
---

# IMAPISession::CompareEntryIDs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
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
  
> One or both of the entry identifiers specified as parameters do not refer to objects, possibly because these objects are currently unopened and unavailable.
    
## Remarks

The **IMAPISession::CompareEntryIDs** method compares two entry identifiers that belong to a single service provider to determine whether they refer to the same object. MAPI extracts the [MAPIUID](mapiuid.md) portion from the entry identifiers to determine the service provider responsible for the objects and then calls its logon object's **CompareEntryIDs** method to perform the comparison. 
  
## Notes to callers

The **CompareEntryIDs** method is useful because an object can have more than one valid entry identifier. This situation can occur, for example, after a new version of a service provider is installed. 
  
If **CompareEntryIDs** returns an error, do not take any action based on the result of the comparison. Instead, take the most conservative approach possible. **CompareEntryIDs** might fail if, for example, one or both of the entry identifiers contain an invalid **MAPIUID**. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|BaseDialog.cpp  <br/> |CbaseDialog::OnCompareEntryIDs  <br/> |MFCMAPI uses the **IMAPISession::CompareEntryIDs** method to compare two entry IDs that a user enters.  <br/> |
   
## See also



[MAPIUID](mapiuid.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

