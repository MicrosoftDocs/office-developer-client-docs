---
title: "CURRENCY"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- CURRENCY
api_type:
- COM
ms.assetid: cffc05a0-95e4-4b9f-bf8f-c4272a75afa8
description: "Last modified: March 09, 2015"
---

# CURRENCY

  
  
**Applies to**: Outlook 
  
Contains a signed 64-bit integer representing a currency value. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct tagCY
{
  unsigned long Lo;
  long Hi;
} CURRENCY;

```

## Members

 **Lo**
  
> Low-order 32 bits of the currency value. 
    
 **Hi**
  
> High-order 32 bits of the currency value.
    
## Remarks

The **CURRENCY** structure is a scaled integer representation of a decimal number with four digits to the right of the decimal point. For example, a stored value of 327500 is to be construed as representing a currency value of 32.7500. 
  
The **CURRENCY** structure is used to describe a property of type PT_CURRENCY. For information about property types, see [MAPI Property Type Overview](mapi-property-type-overview.md).
  
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

