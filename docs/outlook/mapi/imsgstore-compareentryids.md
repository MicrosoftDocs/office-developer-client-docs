---
title: "IMsgStoreCompareEntryIDs"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.CompareEntryIDs
api_type:
- COM
ms.assetid: 33d70748-0d3f-4be4-bcb5-7ec048887944
description: "Last modified: March 09, 2015"
---

# IMsgStore::CompareEntryIDs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two entry identifiers to determine whether they refer to the same entry in a message store. MAPI passes this call to a service provider only if the unique identifiers (UIDs) in both entry identifiers to be compared are handled by that provider.
  
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
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID1_ parameter  _._
    
 _lpEntryID1_
  
> [in] A pointer to the first entry identifier to be compared.
    
 _cbEntryID2_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID2_ parameter  _._
    
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
  
> One or both of the entry identifiers specified as parameters do not refer to objects, possibly because the corresponding objects are unopened and unavailable at present.
    
## Remarks

The **IMsgStore::CompareEntryIDs** method compares two entry identifiers that belong to the message store to determine whether they refer to the same object. 
  
## Notes to callers

 **CompareEntryIDs** is useful because an object can have more than one valid entry identifier (for example, after a new version of a message store provider is installed). 
  
If **CompareEntryIDs** returns an error, do not take any action based on the result of the comparison. Instead, take the most conservative approach possible. **CompareEntryIDs** might fail if, for example, one or both of the entry identifiers contains an invalid **MAPIUID**. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|BaseDialog.cpp  <br/> |CBaseDialog::OnCompareEntryIDs  <br/> |MFCMAPI uses the **IMsgStore::CompareEntryIDs** method to compare entry IDs. |
   
## See also



[MAPIUID](mapiuid.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

