---
title: "SMAPIFormPropArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SMAPIFormPropArray
api_type:
- COM
ms.assetid: bb243bc4-4974-4ad6-aa76-2426c1ebe84b
description: "Last modified: March 09, 2015"
---

# SMAPIFormPropArray

  
  
**Applies to**: Outlook 
  
Contains an array of [SMAPIFormProp](smapiformprop.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Related macro:  <br/> |[CbMAPIFormPropArray](cbmapiformproparray.md) <br/> |
   
```cpp
typedef struct
{
  ULONG cProps;
  ULONG ulPad;
  SMAPIFormProp aFormProp[MAPI_DIM];
} SMAPIFormPropArray, FAR * LPMAPIFORMPROPARRAY;

```

## Members

 **cProps**
  
> Count of named properties in the array in the **aFormProp** member. 
    
 **ulPad**
  
>  Eight bytes of padding used to guarantee correct alignment. 
    
 **aFormProp**
  
> Array of form properties.
    
## Remarks

The **SMAPIFormPropArray** structure is passed as a parameter to the following methods: 
  
- [IMAPIFormInfo::CalcFormPropSet](imapiforminfo-calcformpropset.md)
    
- [IMAPIFormMgr::CalcFormPropSet](imapiformmgr-calcformpropset.md)
    
- [IMAPIFormContainer::CalcFormPropSet](imapiformcontainer-calcformpropset.md)
    
## See also

#### Reference

[CbMAPIFormPropArray](cbmapiformproparray.md)
  
[SMAPIFormProp](smapiformprop.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

