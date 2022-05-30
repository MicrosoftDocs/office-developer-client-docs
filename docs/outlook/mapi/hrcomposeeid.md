---
title: "HrComposeEID"
description: Describes HrComposeEID and provides syntax, parameters, and return value.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.HrComposeEID
api_type:
- COM
ms.assetid: 8aba90d8-ea1f-4636-af80-17bfeadbdfa0
---

# HrComposeEID

**Applies to**: Outlook 2013 | Outlook 2016
  
Creates a compound entry identifier for an object, usually a message in a message store.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |

```cpp
HrComposeEID(
  LPMAPISESSION psession,
  ULONG cbStoreRecordKey,
  LPBYTE pStoreRecordKey,
  ULONG cbMsgEID,
  LPENTRYID pMsgEID,
  ULONG FAR * pcbEID,
  LPENTRYID FAR * ppEID
);
```

## Parameters

 _psession_
  
> [in] Pointer to the session in use by the client application.

 _cbStoreRecordKey_
  
> [in] Size, in bytes, of the record key of the message store holding the message or other object. If zero is passed in the _cbStoreRecordKey_ parameter, the  _ppEID_ parameter points to a copy of the object's entry identifier.

 _pStoreRecordKey_
  
> [in] Pointer to the record key of the message store that contains the message or other object.

 _cbMsgEID_
  
> [in] Size, in bytes, of the entry identifier of the message or other object.

 _pMsgEID_
  
> [in] Pointer to the entry identifier of the object.

 _pcbEID_
  
> [out] Pointer to the size, in bytes, of the returned identifier.

 _ppEID_
  
> [out] Pointer to a pointer to the returned entry identifier. If the value of the  _cbStoreRecordKey_ parameter is greater than zero, the  _ppEID_ parameter points to a pointer to the compound entry identifier that is created. If _cbStoreRecordKey_ is zero, _ppEID_ points to a pointer to a copy of the object's entry identifier.

## Return value

None.
  
## Remarks

If the message or other object for which the compound entry identifier is being created resides in a message store, the identifier is created from the object's entry identifier and the store's record key. If the object is not in a store, that is, if the byte count for the store record key passed in  _cbStoreRecordKey_ is zero, the object's entry identifier is simply copied.
  
The **HrComposeEID** function enables applications to work with objects in multiple stores through the use of compound entry identifiers. An application can call the [HrDecomposeEID](hrdecomposeeid.md) function to split the compound entry identifier into its original constituents.
  
## See also

[HrComposeMsgID](hrcomposemsgid.md)
  
[HrDecomposeMsgID](hrdecomposemsgid.md)
