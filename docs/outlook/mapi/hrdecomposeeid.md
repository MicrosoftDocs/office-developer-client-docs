---
title: "HrDecomposeEID" 
description: This article describes the HrDecomposeEID function and provides syntax, parameters, and return value.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.HrDecomposeEID
api_type:
- COM
ms.assetid: 4847838a-2ad8-4927-8f78-7fa5c8eb54eb
---

# HrDecomposeEID

**Applies to**: Outlook 2013 | Outlook 2016
  
Separates the compound entry identifier of an object, usually a message in a message store, into the entry identifier of that object in the store and the store's entry identifier.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |

```cpp
HrDecomposeEID(
  LPMAPISESSION psession,
  ULONG cbEID,
  LPENTRYID pEID,
  ULONG FAR * pcbStoreEID,
  LPENTRYID FAR * ppStoreEID,
  ULONG FAR * pcbMsgEID,
  LPENTRYID FAR * ppMsgEID
);
```

## Parameters

 _psession_
  
> [in] Pointer to the session in use by the client application.

 _cbEID_
  
> [in] Size, in bytes, of the compound entry identifier to be separated.

 _pEID_
  
> [in] Pointer to the compound entry identifier to be separated.

 _pcbStoreEID_
  
> [out] Pointer to the returned size, in bytes, of the entry identifier of the message store that contains the object. If the _pEID_ parameter points to a noncompound entry identifier, then the  _pcbStoreEID_ parameter points to a value of zero.

 _ppStoreEID_
  
> [out] Pointer to a pointer to the returned entry identifier of the message store that contains the object. If the _pEID_ parameter points to a noncompound entry identifier, NULL is returned in the _ppStoreEID_ parameter.

 _pcbMsgEID_
  
> [out] Pointer to the returned size, in bytes, of the entry identifier of the object. If the _pEID_ parameter points to a noncompound entry identifier, then the _pcbMsgEID_ parameter is equal to the value of the _cbEID_ parameter.

 _ppMsgEID_
  
> [out] Pointer to a pointer to the returned entry identifier of the object. If the _pEID_ parameter points to a noncompound entry identifier, _ppMsgEID_ points to a pointer to a copy of the noncompound entry identifier.

## Return value

None.
  
## Remarks

If the identifier specified by the  _pEID_ parameter is compound, it is split into the entry identifier of the object within its message store and the store's entry identifier. Noncompound entry identifier strings are simply copied. The compound identifier to be separated is usually one created by the [HrComposeEID](hrcomposeeid.md) function.
  
## Notes to callers

The memory that holds the  _pEID_ parameter is released upon successful completion of this function. The calling implementation is responsible for freeing memory for the output parameters.
  