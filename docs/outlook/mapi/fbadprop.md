---
title: "FBadProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- FBadProp
api_type:
- HeaderDef
ms.assetid: 929330c8-e6f2-4adf-a36e-fba18fa055d4
description: "Last modified: March 09, 2015"
---

# FBadProp

  
  
**Applies to**: Outlook 
  
Validates a specified property. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```
ULONG FBadProp(
  LPSPropValue lpprop
);
```

## Parameters

 _lpprop_
  
> [in] An [SPropValue](spropvalue.md) structure defining the property to be validated. 
    
## Return value

TRUE 
  
> The specified property is invalid. 
    
FALSE 
  
> The specified property is valid.
    
## Remarks

A service provider can call the **FBadProp** function for several reasons, for example to prepare for a call to the [IMAPIProp::SetProps](imapiprop-setprops.md) method setting a property. **FBadProp** validates the specified property depending on the property type. For example, if the property is Boolean, **FBadProp** make sures that its value is either TRUE or FALSE. If the property is binary, **FBadProp** checks its pointer and size and makes sure that it is allocated correctly. 
  
## See also

#### Reference

[FBadPropTag](fbadproptag.md)

