---
title: "CURRENCY"
description: "CURRENCY contains a signed 64-bit integer representing a currency value. This article describes its members and remarks."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- CURRENCY
api_type:
- COM
ms.assetid: cffc05a0-95e4-4b9f-bf8f-c4272a75afa8
---

# CURRENCY

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a signed 64-bit integer representing a currency value. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
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



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

