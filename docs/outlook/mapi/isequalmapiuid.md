---
title: "IsEqualMAPIUID"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.IsEqualMAPIUID
api_type:
- COM
ms.assetid: 85d71b73-0630-4c5d-b0e3-b48d27a300d0
description: "Last modified: March 09, 2015"
---

# IsEqualMAPIUID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Tests two [MAPIUID](mapiuid.md) structures to determine whether they contain the same identifier. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**MAPIUID** <br/> |
   
```cpp
IsEqualMAPIUID(lpuid1, lpuid2)
```

## Parameters

 _lpuid1_
  
> Pointer to the first **MAPIUID** structure to be tested. 
    
 _lpuid2_
  
> Pointer to the second **MAPIUID** structure to be tested. 
    
## Remarks

The **IsEqualMAPIUID** macro returns TRUE if the two **MAPIUID** structures contain the same identifier and FALSE if they do not. 
  
The **IsEqualMAPIUID** macro requires that the header file Memory.h be included. 
  
## See also



[MAPIUID](mapiuid.md)


[Macros Related to Structures](macros-related-to-structures.md)

