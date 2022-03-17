---
title: "HrGetOneProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- HrGetOneProp
api_type:
- HeaderDef
ms.assetid: 8d0a381a-e714-4663-9a57-b0e1cdbd6ba7
description: "Last modified: March 09, 2015"
---

# HrGetOneProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the value of a single property from a property interface, that is, an interface derived from [IMAPIProp](imapipropiunknown.md). 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrGetOneProp(
  LPMAPIPROP pmp,
  ULONG ulPropTag,
  LPSPropValue FAR * ppprop
);
```

## Parameters

 _pmp_
  
> [in] Pointer to the [IMAPIProp](imapipropiunknown.md) interface from which the property value is to be retrieved. 
    
 _ulPropTag_
  
> [in] Property tag of the property to be retrieved. 
    
 _ppprop_
  
> [out] Pointer to a pointer to the returned [SPropValue](spropvalue.md) structure defining the retrieved property value. 
    
## Return value

MAPI_E_NOT_FOUND 
  
> The requested property is not available from the specified interface.
    
## Remarks

Unlike the [IMAPIProp::GetProps](imapiprop-getprops.md) method, the **HrGetOneProp** function never returns any warning. Because it retrieves only one property, it simply either succeeds or fails. For retrieving multiple properties, **GetProps** is faster. 
  
You can set or change a single property with the [HrSetOneProp](hrsetoneprop.md) function. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |GetMAPIObjectType  <br/> |MFCMAPI uses the **HrGetOneProp** method to retrieve the type of an object. |
   
## See also



[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

