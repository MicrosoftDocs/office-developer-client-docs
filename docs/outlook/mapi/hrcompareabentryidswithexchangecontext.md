---
title: "HrCompareABEntryIDsWithExchangeContext"
description: The HrCompareABEntryIDsWithExchangeContext function compares two address book entryIDs safely in a Multiple Exchange profile.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: e537c25f-51b5-4f06-a20a-44ee540b9a1f
---

# HrCompareABEntryIDsWithExchangeContext

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two address book **entryIDs** safely in a Multiple Exchange profile. This function is a replacement function for [IAddrBook::CompareEntryIDs](iaddrbook-compareentryids.md).
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |abhelp.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrCompareABEntryIDsWithExchangeContext(
  LPMAPISESSION pmsess,
  const MAPIUID *pEmsmdbUID,
  LPADRBOOK pAddrBook,
  ULONG cbEntryID1,
  LPENTRYID lpEntryID1,
  ULONG cbEntryID2,
  LPENTRYID lpEntryID2,
  ULONG ulFlags,
  ULONG * lpulResult
);
```

## Parameters

 _pmsess_
  
> [in] The logged on **IMAPISession**. It cannot be NULL.
    
 _pEmsmdbUID_
  
> [in] A pointer to an **emsmdbUID** that identifies the Exchange Service that contains the Exchange Address Book Provider that this function should use to display details on the entry identifier. If the incoming entry identifier is not an Exchange Address Book Provider entry identifier, this parameter is ignored and the function call behaves like [IAddrBook::Details](iaddrbook-details.md). If this parameter is NULL or a zero MAPIUID, this function behaves like [IAddrBook::Details](iaddrbook-details.md).
    
 _pAddrBook_
  
> [in] The address book used to open the entry identifier. It cannot be NULL.
    
 _cbEntryID1_
  
> [in] The byte count of the first entry identifier specified by the  _lpEntryID1_ parameter. 
    
 _lpEntryID1_
  
> [in] A pointer to the first entry identifier that represents the address book entry to compare.
    
 _cbEntryID2_
  
> [in] The byte count of the second entry identifier specified by the  _lpEntryID2_ parameter. 
    
 _lpEntryID2_
  
> [in] A pointer to the second entry identifier used in the comparison that represents the address book entry to compare.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpulResult_
  
> [out] A pointer to the location that contains the results of the comparison. 
    

