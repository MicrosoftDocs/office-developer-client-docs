---
title: "SBinary"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SBinary
api_type:
- COM
ms.assetid: f21b5e6c-7a63-46bf-acbf-0e042e3519f7
description: "Last modified: March 09, 2015"
---

# SBinary

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Describes a property of type PT_BINARY.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _SBinary
{
  ULONG      cb;
  LPBYTE     lpb;
} SBinary, FAR *LPSBinary;

```

## Members

 **cb**
  
> Count of bytes in the **lpb** member. 
    
 **lpb**
  
> Pointer to the PT_BINARY property value.
    
## Remarks

For information about property types, see [MAPI Property Type Overview](mapi-property-type-overview.md).
  
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

