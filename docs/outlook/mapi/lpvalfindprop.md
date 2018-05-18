---
title: "LpValFindProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 67461a38-bb60-467b-901b-39c645e764f7
description: "Last modified: March 09, 2015"
---

# LpValFindProp

  
  
**Applies to**: Outlook 
  
Searches for a specified property in a property set.
  
|||
|:-----|:-----|
|Header file:  <br/> |mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers.  <br/> |
   
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

