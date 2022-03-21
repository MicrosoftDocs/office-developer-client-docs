---
title: "HrGetGALFromEmsmdbUID"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 9b824e70-ed9a-490c-b777-8902a793fece
description: "Last modified: March 09, 2015"
---

# HrGetGALFromEmsmdbUID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the entry identifier of the global address book for the Exchange service identified by  _pEmsmdbUID_. The returned entry identifier should be freed using [MAPIFreeBuffer](mapifreebuffer.md).
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |abhelp.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrGetGALFromEmsmdbUID(
  LPMAPISESSION pSess,
  LPADRBOOK lpAdrBook,
  const MAPIUID * pEmsmdbUID,
  ULONG * lpcbeid,
  LPENTRYID * lppeid
);
```

## Parameters

 _pSess_
  
> [in] The logged on IMAPISession. It cannot be NULL.
    
 _pAddrBook_
  
> [in] The address book used to open the entry identifier. It cannot be NULL.
    
 _pEmsmdbUID_
  
> [in] A pointer to an **emsmdbUID** that identifies the GAL of the Exchange Service to be retrieved. If  _pEmsmdbUID_ is NULL or the zero UID, this function gets the legacy GAL of the Exchange Service. 
    
 _lpcbeid_
  
> [out] A pointer to the byte count of the entry identifier of the global address list.
    
 _lppeid_
  
> [out] A pointer to the entry identifier of the global address list. This should be freed using [MAPIFreeBuffer](mapifreebuffer.md).
    

