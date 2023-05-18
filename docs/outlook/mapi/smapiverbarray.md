---
title: "SMAPIVerbArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SMAPIVerbArray
api_type:
- COM
ms.assetid: 8736f75c-3e95-42dd-9bc1-2f0bd23c4a02
description: "Contains an array of SMAPIVerb structures that describe MAPI verbs for Outlook 2013 and Outlook 2016."
---

# SMAPIVerbArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of [SMAPIVerb](smapiverb.md) structures that describe MAPI verbs. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Related macro:  <br/> |[CbMAPIVerbArray](cbmapiverbarray.md) <br/> |
   
```cpp
typedef struct
{
  ULONG cMAPIVerb;
  SMAPIVerb aMAPIVerb[MAPI_DIM];
} SMAPIVerbArray, FAR * LPMAPIVERBARRAY;

```

## Members

 **cForms**
  
> Count of verbs in the array.
    
 **aFormInfo**
  
> Array of MAPI verbs.
    
## Remarks

The **SMAPIVerbArray** structure is passed as a parameter in the [IMAPIFormInfo::CalcVerbSet](imapiforminfo-calcverbset.md) method. 
  
## See also



[SMAPIVerb](smapiverb.md)


[MAPI Structures](mapi-structures.md)

