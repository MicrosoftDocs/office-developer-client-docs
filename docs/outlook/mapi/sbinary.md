---
title: "SBinary"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SBinary
api_type:
- COM
ms.assetid: f21b5e6c-7a63-46bf-acbf-0e042e3519f7
description: "Last modified: March 09, 2015"
---

# SBinary

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a property of type PT_BINARY.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
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



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

