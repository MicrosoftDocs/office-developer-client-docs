---
title: "SBinaryArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SBinaryArray
api_type:
- COM
ms.assetid: 2d5b7302-cad2-4522-beb1-7c6c711f42e6
description: "Last modified: March 09, 2015"
---

# SBinaryArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of binary values. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SBinaryArray
{
  ULONG cValues;
  SBinary FAR *lpbin;
} SBinaryArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpbin** member. 
    
 **lpbin**
  
> Pointer to an array of [SBinary](sbinary.md) structures that holds the binary values. 
    
## Remarks

The **SBinaryArray** structure is used to describe properties of type PT_MV_BINARY. 
  
For more information about PT_MV_BINARY, see [List of Property Types](property-types.md).
  
## See also



[SBinary](sbinary.md)
  
[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

