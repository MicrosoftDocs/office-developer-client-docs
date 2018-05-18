---
title: "HrComposeMsgID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.HrComposeMsgID
api_type:
- COM
ms.assetid: bb76b147-6552-4cc4-920f-699170aea17f
description: "Last modified: March 09, 2015"
---

# HrComposeMsgID

  
  
**Applies to**: Outlook 
  
Creates an ASCII string representing a compound entry identifier for an object, usually a message in a message store. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
HrComposeMsgID(
  LPMAPISESSION psession,
  ULONG cbStoreRecordKey,
  LPBYTE pStoreRecordKey,
  ULONG cbMsgEID,
  LPENTRYID pMsgEID,
  LPSTR FAR * pszMsgID
);
```

## Parameters

 _psession_
  
> [in] Pointer to the session in use by the client application. 
    
 _cbStoreRecordKey_
  
> [in] Size, in bytes, of the record key of the message store that contains the message or other object. If zero is passed in the  _cbStoreRecordKey_ parameter, the  _pszMsgID_ parameter points to a copy of the entry identifier converted to text. 
    
 _pStoreRecordKey_
  
> [in] Pointer to the record key of the message store that contains the message or other object. 
    
 _cbMsgEID_
  
> [in] Size, in bytes, of the entry identifier of the message or other object. 
    
 _pMsgEID_
  
> [in] Pointer to the entry identifier of the object. 
    
 _pszMsgID_
  
> [out] Pointer to the returned ASCII string. If the  _cbStoreRecordKey_ parameter is greater than zero, the  _pszMsgID_ parameter points to a compound entry identifier converted to text. If  _cbStoreRecordKey_ is zero,  _pszMsgID_ points to a noncompound entry identifier converted to text. 
    
## Return value

None.
  
## Remarks

If the message or other object for which the compound entry identifier is being created resides in a message store, the identifier string is created from the object's entry identifier and the store's record key. If the object is not in a store, that is, if the byte count for the store record key passed in the  _cbStoreRecordKey_ parameter is zero, the object's entry identifier is simply copied and converted into a string. 
  
Calling the **HrComposeMsgID** function is equivalent to calling the [HrComposeEID](hrcomposeeid.md) function and then the [HrSzFromEntryID](hrszfromentryid.md) function. 
  
 **HrComposeMsgID** enables client applications to work with objects in multiple stores through the use of compound entry identifiers. An application can call the [HrDecomposeMsgID](hrdecomposemsgid.md) function to split the compound entry identifier into its original constituents. 
  

