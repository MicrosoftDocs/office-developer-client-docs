---
title: "IPropDataHrAddObjProps"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPropData.HrAddObjProps
api_type:
- COM
ms.assetid: 683cf476-3c02-4b3b-939f-6fff6611f9aa
description: "Last modified: July 23, 2011"
---

# IPropData::HrAddObjProps

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Adds one or more properties of type PT_OBJECT to the object.
  
```
HRESULT HrAddObjProps(
  LPSPropTagArray lpPropTagArray,
  LPSPropProblemArray FAR * lppProblems
);
```

## Parameters

 _lpPropTagArray_
  
> [in] A pointer to an array of property tags that indicate the properties to add.
    
 _lppProblems_
  
> [in, out] On input, a valid pointer to an [SPropProblemArray](spropproblemarray.md) structure, or NULL. On output, a pointer to a pointer to a structure that contains information about properties that could not be added, or NULL. A pointer to a property problem array structure is returned only if a valid pointer is passed in. 
    
## Return value

S_OK 
  
> The properties were successfully added.
    
MAPI_E_INVALID_TYPE 
  
> A property type other than PT_OBJECT was passed in the array that the  _lpPropTagArray_ parameter points to. 
    
MAPI_E_NO_ACCESS 
  
> The object has been set not to allow read/write permission.
    
MAPI_W_PARTIAL_COMPLETION 
  
> Some, but not all, of the properties were added.
    
## Remarks

The **IPropData::HrAddObjProps** method adds one or more properties of type PT_OBJECT to the object. **HrAddObjProps** provides an alternative to the [IMAPIProp::SetProps](imapiprop-setprops.md) method for object properties, because object properties cannot be created by calling **SetProps**. Adding an object property results in the property tag being included in the list of property tags that the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method returns. 
  
## Notes to Callers

If **HrAddObjProps** returns MAPI_W_PARTIAL_COMPLETION and you have set  _lppProblems_ to a valid pointer, check the returned [SPropProblemArray](spropproblemarray.md) structure to find out which properties were not added. Typically, the only problem that occurs is lack of memory. Free the **SPropProblemArray** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function when you are finished with it. 
  
To add a property, the target object must have read/write permission. If **HrAddObjProps** returns MAPI_E_NO_ACCESS, you cannot add properties to the object because it does not permit modification. To obtain read/write permission to an object prior to calling **HrAddObjProps**, call [IPropData::HrSetObjAccess](ipropdata-hrsetobjaccess.md) and set the  _ulAccess_ parameter to IPROP_READWRITE. 
  
## See also

#### Reference

[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropProblemArray](spropproblemarray.md)
  
[SPropTagArray](sproptagarray.md)
  
[IPropData : IMAPIProp](ipropdataimapiprop.md)

