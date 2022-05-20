---
title: "SCurrencyArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SCurrencyArray
api_type:
- COM
ms.assetid: d28852ab-b542-40e1-b2ec-85d20a2eddfd
description: "Contains an array of currency values that are used to describe a property of type PT_MV_CURRENCY."
---

# SCurrencyArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of currency values that are used to describe a property of type PT_MV_CURRENCY. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SCurrencyArray
{
  ULONG         cValues;
  CURRENCY FAR *lpcur;
} SCurrencyArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpcur** member. 
    
 **lpcur**
  
> Pointer to an array of [CURRENCY](currency.md) structures that contain the currency values. 
    
## Remarks

For information about PT_MV_CURRENCY, see [List of Property Types](property-types.md). 
  
## See also



[CURRENCY](currency.md)
  
[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

