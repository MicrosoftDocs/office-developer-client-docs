---
title: "IMSLogonCompareEntryIDs"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMSLogon.CompareEntryIDs
api_type:
- COM
ms.assetid: 481812d6-8e94-4510-b288-55501dd5757c
description: "Last modified: July 23, 2011"
---

# IMSLogon::CompareEntryIDs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two entry identifiers to determine whether they refer to the same object. MAPI refers this call to a service provider only if the unique identifiers (UIDs) in both entry identifiers to be compared are handled by that provider.
  
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

Message store providers implement the **IMSLogon::CompareEntryIDs** method to compare two entry identifiers for a given entry in a message store to determine whether they refer to the same object. If the two entry identifiers refer to the same object, **CompareEntryIDs** sets the  _lpulResult_ parameter to TRUE; if they refer to different objects, **CompareEntryIDs** sets  _lpulResult_ to FALSE. 
  
 **CompareEntryIDs** is useful because an object can have more than one valid entry identifier. This can occur, for example, after a new version of a message store provider is installed. 
  
## See also



[IMSLogon : IUnknown](imslogoniunknown.md)

