---
title: "FEqualNames"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FEqualNames
api_type:
- COM
ms.assetid: 4dd58b0b-dc39-4782-a9ec-05e353c90927
description: "Last modified: March 09, 2015"
---

# FEqualNames

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Determines whether two MAPI named properties are the same. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
BOOL FEqualNames(
  LPMAPINAMEID lpName1,
  LPMAPINAMEID lpName2
);
```

## Parameters

 _lpName1_
  
> [in] Pointer to a [MAPINAMEID](mapinameid.md) structure describing the first named property. 
    
 _lpName2_
  
> [in] Pointer to a **MAPINAMEID** structure describing the second named property. 
    
## Return value

TRUE 
  
> The two property names are equal. 
    
FALSE 
  
> The two property names are not equal.
    
## Remarks

The **FEqualNames** function is useful because the **MAPINAMEID** structure contains a [GUID](guid.md) and can represent the property name itself in more than one way. This means the two structures cannot be compared by simple binary methods. 
  
The testing process is case-sensitive for the property name strings. 
  

