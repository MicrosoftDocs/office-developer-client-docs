---
title: "FPropCompareProp"
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FPropCompareProp
api_type:
- COM
ms.assetid: 17cb53c4-7154-4a4e-b4ec-de720fa055cb
description: "Compares two property values using a specified relational operator."
---

# FPropCompareProp

**Applies to**: Outlook 2013 | Outlook 2016
  
Compares two property values using a specified relational operator.
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |

```cpp
BOOL FPropCompareProp(
  LPSPropValue lpSPropValue1,
  ULONG ulRelOp,
  LPSPropValue lpSPropValue2
);
```

## Parameters

_lpSPropValue1_
  
> [in] Pointer to an [SPropValue](spropvalue.md) structure defining the first property value for comparison.

_ulRelOp_
  
> [in] The relational operator to use in the comparison. For allowable values, see the [SComparePropsRestriction](scomparepropsrestriction.md) structure.

_lpSPropValue2_
  
> [in] Pointer to an **SPropValue** structure defining the second property value for comparison.

## Return value

TRUE
  
> The property values satisfy the specified relation.

FALSE
  
> The property values do not satisfy the specified relation.

## Remarks

The comparison method depends on the property types specified in the [SPropValue](spropvalue.md) property definitions. The **FPropCompareProp** and [FPropContainsProp](fpropcontainsprop.md) functions can be used to prepare restrictions for generating a table.
  
The order of comparison is _lpSPropValue1_, _ulRelOp_, _lpSPropValue2_. If the property types of the property values to be compared do not match, the **FPropCompareProp** function returns FALSE.
