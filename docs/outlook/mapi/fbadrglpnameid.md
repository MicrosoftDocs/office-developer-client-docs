---
title: "FBadRglpNameID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FBadRglpNameID
api_type:
- COM
ms.assetid: fec5d5ac-bca6-4fff-b264-45cdb6b37f55
description: "Last modified: March 09, 2015"
---

# FBadRglpNameID

  
  
**Applies to**: Outlook 
  
Validates an array of structures that describe named properties and verifies their allocation. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
BOOL FBadRglpNameID(
  LPMAPINAMEID FAR * lppNameId,
  ULONG cNames
);
```

## Parameters

 _lppNameId_
  
> [in] Pointer to an array of [MAPINAMEID](mapinameid.md) structures describing the named properties. 
    
 _cNames_
  
> [in] Count of named property structures in the array pointed to by the  _lppNameId_ parameter. 
    
## Return value

TRUE 
  
> One or more of the specified property name structures is invalid. 
    
FALSE 
  
> The specified property name structures are all valid.
    
## Remarks

The **FBadRglpNameID** function can be used when setting up for a call to [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) or [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md). 
  

