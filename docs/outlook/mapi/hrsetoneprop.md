---
title: "HrSetOneProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.HrSetOneProp
api_type:
- COM
ms.assetid: 14ae3242-fddf-4199-a9a7-4ab153b31064
description: "Last modified: March 09, 2015"
---

# HrSetOneProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets or changes the value of a single property on a property interface, that is, an interface derived from [IMAPIProp](imapipropiunknown.md). 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrSetOneProp(
  LPMAPIPROP pmp,
  LPSPropValue pprop
);
```

## Parameters

 _pmp_
  
> [in] Pointer to an [IMAPIProp](imapipropiunknown.md) interface on which the property value is to be set or changed. 
    
 _pprop_
  
> [in] Pointer to the [SPropValue](spropvalue.md) structure defining the value to be set on the  _pmp_ property. 
    
## Return value

None.
  
## Remarks

Unlike the [IMAPIProp::SetProps](imapiprop-setprops.md) method, the **HrSetOneProp** function never returns any warnings. Because it sets only one property, it simply either succeeds or fails. For setting or changing multiple properties, **SetProps** is faster. 
  
You can retrieve a single property with the [HrGetOneProp](hrgetoneprop.md) function. 
  

