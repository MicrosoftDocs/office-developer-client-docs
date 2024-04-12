---
title: "PpropFindProp"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PpropFindProp
api_type:
- HeaderDef
ms.assetid: f23dd6f4-915b-4fe8-ab3f-6d625c7d6061
description: "Searches for a specified property in a property set for Outlook 2013 and Outlook 2016."
---

# PpropFindProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Searches for a specified property in a property set.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
LPSPropValue PpropFindProp(
  LPSPropValue rgprop,
  ULONG cprop,
  ULONG ulPropTag
);
```

## Parameters

 _rgprop_
  
> [in] Array of [SPropValue](spropvalue.md) structures that define the properties to be searched. 
    
 _cprop_
  
> [in] Count of properties in the property set indicated by the  _rgprop_ parameter. 
    
 _ulPropTag_
  
> [in] Property tag for the property to search for in the property set indicated by the  _rgprop_ parameter. 
    
## Return value

 **PpropFindProp** returns an [SPropValue](spropvalue.md) structure defining the property that matches the input property tag, or NULL if there is no match. 
  
## Remarks

If the given property tag indicates a property of type PT_UNSPECIFIED, the **PpropFindProp** function finds a match only for the property identifier in the tag. Otherwise, it finds a match for the entire property tag, including the property type, and returns the property identified. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::BuildDataItem  <br/> |MFCMAPI uses the **PpropFindProp** method to find properties in a property set being added to the list. |
   
## See also



[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

