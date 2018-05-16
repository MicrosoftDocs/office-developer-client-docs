---
title: "HrDecomposeMsgID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.HrDecomposeMsgID
api_type:
- COM
ms.assetid: 5e6a9f3e-79be-4ffd-9d42-3a14cabb1435
description: "Last modified: March 09, 2015"
---

# HrDecomposeMsgID

  
  
**Applies to**: Outlook 
  
Separates the ASCII representation of the compound entry identifier of an object, usually a message in a message store, into the entry identifier of that object in the store and the store's entry identifier. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```
HrDecomposeMsgID(
  LPMAPISESSION psession,
  LPSTR szMsgID,
  ULONG FAR * pcbStoreEID,
  LPENTRYID FAR * ppStoreEID,
  ULONG FAR * pcbMsgEID,
  LPENTRYID FAR * ppMsgEID
);
```

## Parameters

 _psession_
  
> [in] Pointer to the session in use by the client application. 
    
 _szMsgID_
  
> [in] The string representing the entry identifier of the object. 
    
 _pcbStoreEID_
  
> [out] Pointer to the returned size, in bytes, of the entry identifier of the message store that contains the object. If the  _szMsgID_ parameter points to a noncompound entry identifier string, then the  _pcbStoreEID_ parameter points to zero. 
    
 _ppStoreEID_
  
> [out] Pointer to a pointer to the returned entry identifier of the message store that contains the object. If the  _szMsgID_ parameter points to a noncompound entry identifier, NULL is returned in the  _ppStoreEID_ parameter. 
    
 _pcbMsgEID_
  
> [out] Pointer to the returned size, in bytes, of the entry identifier of the object within its store. If the  _szMsgID_ parameter points to a noncompound entry identifier string, then the  _pcbMsgEID_ parameter is equal to the value of the  _cbEID_ parameter. 
    
 _ppMsgEID_
  
> [out] Pointer to a pointer to the returned entry identifier string of the object within its store. If the  _szMsgID_ parameter points to a noncompound entry identifier,  _ppMsgEID_ points to a pointer to a converted copy of the noncompound entry identifier. 
    
## Return value

None.
  
## Remarks

If the identifier specified by the  _szMsgID_ parameter is compound, it is converted from ASCII and split into the entry identifier of the object within its message store and the store's entry identifier. Noncompound entry identifier strings are simply converted and copied. The compound identifier string to be separated is usually one created by the [HrComposeMsgID](hrcomposemsgid.md) function. 
  
Calling the **HrDecomposeMsgID** function is equivalent to calling the [HrEntryIDFromSz](hrentryidfromsz.md) function and then the [HrDecomposeEID](hrdecomposeeid.md) function. 
  

