---
title: "LpValFindProp"
description: Describes the LpValFindProp function and provides, syntax, parameters, return value, and additional remarks.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 67461a38-bb60-467b-901b-39c645e764f7
---

# LpValFindProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Searches for a specified property in a property set.
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers. |
   
```cpp
LPSPropValue LpValFindProp(
  ULONG ulPropTag,
  ULONG cValues,
  LPSPropValue lpPropArray
);
```

## Parameters

 _ulPropTag_
  
> [in] Tag for the property to search for in the property set, indicated by the  _lpPropArray_ parameter. 
    
 _cValues_
  
> [in] Count of properties in the property set, indicated by the  _lpPropArray_ parameter. 
    
 _lpPropArray_
  
> [in] Array of **SPropValue** structures that defines the properties to be searched. 
    
## Return value

The **LpValFindProp** function returns an **SPropValue** structure that defines the property that matches the input property tag, or NULL if there is no match. 
  
## Remarks

The **LpValFindProp** function is identical to **PpropFindProp**.
  
## See also



[PpropFindProp](ppropfindprop.md)
  
[SPropValue](spropvalue.md)

