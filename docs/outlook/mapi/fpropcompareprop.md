---
title: "FPropCompareProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FPropCompareProp
api_type:
- COM
ms.assetid: 17cb53c4-7154-4a4e-b4ec-de720fa055cb
description: "Last modified: March 09, 2015"
---

# FPropCompareProp

  
  
**Applies to**: Outlook 
  
Compares two property values using a specified relational operator. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
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
  
The order of comparison is  _lpSPropValue1_, _ ulRelOp _, _ lpSPropValue2 _. If the property types of the property values to be compared do not match, the **FPropCompareProp** function returns FALSE. 
  

