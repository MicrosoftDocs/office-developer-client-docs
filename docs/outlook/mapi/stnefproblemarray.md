---
title: "STnefProblemArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.STnefProblemArray
api_type:
- COM
ms.assetid: 115d845b-4168-4d49-b880-219ee28baa9a
description: "Last modified: March 09, 2015"
---

# STnefProblemArray

  
  
**Applies to**: Outlook 
  
Contains an array of **STnefProblem** structures describing one or more processing problems that occurred during the encoding or decoding of a Transport Neutral Encapsulation Format (TNEF) stream. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Tnef.h  <br/> |
   
```cpp
typedef struct _STnefProblemArray
{
  ULONG cProblem;
  STnefProblem aProblem[MAPI_DIM];
}STnefProblemArray, FAR * LPSTnefProblemArray

```

## Members

 **cProblem**
  
> Count of elements in the array specified in the **aProblem** member. 
    
 **aProblem**
  
> Array of [STnefProblem](stnefproblem.md) structures. Each structure contains information about a property or attribute processing problem. 
    
## Remarks

If a problem occurs during attribute or property processing, an output parameter in the [ITnef::ExtractProps](itnef-extractprops.md) method and in the [ITnef::Finish](itnef-finish.md) method each receive a pointer to an **STnefProblemArray** structure and **ExtractProps** and **Finish** each return the value MAPI_W_ERRORS_RETURNED. This error value indicates that a problem arose during processing and an **STnefProblemArray** structure was generated. 
  
If an **STnefProblem** structure is not generated during the processing of an attribute or property, the client application can continue under the assumption that the processing of that attribute or property succeeded. The only exception occurs when the problem arose during decoding of an encapsulation block. If the error occurred during this decoding, MAPI_E_UNABLE_TO_COMPLETE can be returned as the [SCODE](scode.md) in the structure. In this case, the decoding of the component corresponding to the block is stopped and decoding is continued in another component. 
  
## See also



[STnefProblem](stnefproblem.md)
  
[SCODE](scode.md)


[MAPI Structures](mapi-structures.md)

