---
title: "IMAPIPropSetProps"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProp.SetProps
api_type:
- COM
ms.assetid: 49f007c9-42e5-4391-8b83-988c9b0ebdba
description: "Last modified: March 09, 2015"
---

# IMAPIProp::SetProps

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Updates one or more properties.
  
```cpp
HRESULT SetProps(
  ULONG cValues,
  LPSPropValue lpPropArray,
  LPSPropProblemArray FAR * lppProblems
);
```

## Parameters

 _cValues_
  
> [in] The count of property values pointed to by the  _lpPropArray_ parameter. The  _cValues_ parameter must not be 0. 
    
 _lpPropArray_
  
> [in] A pointer to an array of [SPropValue](spropvalue.md) structures that contain property values to be updated. 
    
 _lppProblems_
  
> [in, out] On input, a pointer to a pointer to an [SPropProblemArray](spropproblemarray.md) structure; otherwise, NULL, indicating no need for error information. If  _lppProblems_ is a valid pointer on input, **SetProps** returns detailed information about errors in updating one or more properties. 
    
## Return value

S_OK 
  
> The properties were successfully updated.
    
The following values can be returned in the **SPropProblemArray** structure, but not as return values for **SetProps**:
  
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_COMPUTED 
  
> The property cannot be updated because it is read-only, computed by the service provider that is responsible for the object.
    
MAPI_E_INVALID_TYPE 
  
> The property type is invalid.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to modify a read-only object or to access an object for which the user has insufficient permissions.
    
MAPI_E_NOT_ENOUGH_MEMORY 
  
> The property cannot be updated because it is larger than the remote procedure call (RPC) buffer size.
    
MAPI_E_UNEXPECTED_TYPE 
  
> The property type is not the type expected by the calling implementation.
    
## Notes to implementers

Ignore the **PR_NULL** ([PidTagNull](pidtagnull-canonical-property.md)) property tag and all properties with a type of **PT_ERROR**. Do not make changes or report problems in the **SPropProblemArray** structure. 
  
Return MAPI_E_INVALID_PARAMETER if a property of type **PT_OBJECT** is included in the property value array. Also return this error if a multiple-value property is included in the array and its **cValues** member is set to 0. 
  
If the call succeeds overall but there are problems with setting some of the properties, return S_OK and put information about the problems in the appropriate entry of the **SPropProblemArray** structure that the  _lppProblems_ parameter points to. 
  
## Notes to callers

Depending on the service provider, you might also be able to change the property type by passing a property tag that contains a different type than was previously used with a given property identifier.
  
If you include a property tag for a property that is unsupported by the object and the implementation of **SetProps** allows the creation of new properties, the property is added to the object. Any previous value stored with the property identifier that was used for the new property is discarded. 
  
Note that the S_OK return value does not guarantee that all of the properties were successfully updated. Some providers cache **SetProps** calls until they receive a call that requires provider intervention, such as [IMAPIProp::SaveChanges](imapiprop-savechanges.md) or [IMAPIProp::GetProps](imapiprop-getprops.md). Therefore, it is possible to receive error values that relate to the **SetProps** call with the later calls. 
  
If **SetProps** returns S_OK, check the **SPropProblemArray** structure pointed to by  _lppProblems_ for problems updating individual properties. If **SetProps** returns an error, do not check the property problem array. Instead, call the object's [IMAPIProp::GetLastError](imapiprop-getlasterror.md) method. 
  
When updating large properties, **SetProps** can fail and return MAPI_E_NOT_ENOUGH_MEMORY. There is no maximum size for properties, and different objects can have different limits. If you deal with potentially large properties, be prepared to call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method with IID_IStream as the interface identifier if **SetProps** returns this error value. 
  
Call the [MAPIFreeBuffer](mapifreebuffer.md) function to free the **SPropProblemArray** structure. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|PropertyEditor.cpp  <br/> |CPropertyEditor::WriteSPropValueToObject  <br/> |MFCMAPI uses the **IMAPIProp::SetProps** method to write a property back to an object after the property has been edited.  <br/> |
   
## See also



[IMAPIProp::GetLastError](imapiprop-getlasterror.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPIProp::OpenProperty](imapiprop-openproperty.md)
  
[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropProblemArray](spropproblemarray.md)
  
[SPropValue](spropvalue.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)

