---
title: "LPropCompareProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.LPropCompareProp
api_type:
- COM
ms.assetid: f14ad568-fe45-4875-957d-415d39dc6f28
description: "Last modified: March 09, 2015"
---

# LPropCompareProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two property values to determine whether they are equal. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
LONG LPropCompareProp(
  LPSPropValue lpSPropValueA,
  LPSPropValue lpSPropValueB
);
```

## Parameters

 _lpSPropValueA_
  
> [in] Pointer to an [SPropValue](spropvalue.md) structure defining the first property value to be compared. 
    
 _lpSPropValueB_
  
> [in] Pointer to an **SPropValue** structure defining the second property value to be compared. 
    
## Return value

 **LPropCompareProp** returns one of the following values for most property types: 
  
- Less than zero if the value indicated by the  _lpSPropValueA_ parameter is less than that indicated by the  _lpSPropValueB_ parameter. 
    
- Greater than zero if the value indicated by  _lpSPropValueA_ is greater than that indicated by  _lpSPropValueB_.
    
- Zero if the value indicated by  _lpSPropValueA_ equals the value indicated by  _lpSPropValueB_. 
    
For property types that have no intrinsic ordering, such as Boolean or error types, the **LPropCompareProp** function returns an undefined value if the two property values are not equal. This undefined value is nonzero and consistent across calls. 
  
## Remarks

Use the **LPropCompareProp** function only if the types of the two properties to be compared are the same. 
  
Before calling **LPropCompareProp**, a client application or service provider must first retrieve the properties for comparison with a call to the [IMAPIProp::GetProps](imapiprop-getprops.md) method. When a client or provider calls **LPropCompareProp**, the function first examines the property tags to make sure that the comparison of property values is valid. The function then compares the property values, returning an appropriate value. 
  
If the property values are unequal, **LPropCompareProp** determines which one is the greater. The properties that **LPropCompareProp** compares do not have to belong to the same object. 
  

