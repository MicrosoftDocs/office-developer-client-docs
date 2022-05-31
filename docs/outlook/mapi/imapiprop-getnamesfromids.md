---
title: "IMAPIPropGetNamesFromIDs"
description: "IMAPIPropGetNamesFromIDs provides the property names that correspond to one or more property identifiers."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProp.GetNamesFromIDs
api_type:
- COM
ms.assetid: 3efa4731-cf32-4a6c-9ba8-d059e58b0d98
---

# IMAPIProp::GetNamesFromIDs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides the property names that correspond to one or more property identifiers.
  
```cpp
HRESULT GetNamesFromIDs(
  LPSPropTagArray FAR * lppPropTags,
  LPGUID lpPropSetGuid,
  ULONG ulFlags,
  ULONG FAR * lpcPropNames,
  LPMAPINAMEID FAR * FAR * lpppPropNames
);
```

## Parameters

 _lppPropTags_
  
> [in, out] On input, a pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags; otherwise, NULL, indicating that all names should be returned. The **cValues** member for the property tag array cannot be 0. If  _lppPropTags_ is a valid pointer on input, **GetNamesFromIDs** returns names for each property identifier included in the array. 
    
 _lpPropSetGuid_
  
> [in] A pointer to a GUID, or [GUID](guid.md) structure, that identifies a property set. The  _lpPropSetGuid_ parameter can point to a valid property set or can be NULL. 
    
 _ulFlags_
  
> [in] A bitmask of flags that indicates the type of names to be returned. The following flags can be used (if both flags are set, no names will be returned):
    
MAPI_NO_IDS 
  
> Requests that only names stored as Unicode strings be returned. 
    
MAPI_NO_STRINGS 
  
> Requests that only names stored as numeric identifiers be returned. 
    
 _lpcPropNames_
  
> [out] A pointer to a count of the property name pointers in the array pointed to by the  _lppPropNames_ parameter. 
    
 _lpppPropNames_
  
> [out] A pointer to an array of pointers to [MAPINAMEID](mapinameid.md) structures that contains property names. 
    
## Return value

S_OK 
  
> The property names were successfully returned. 
    
MAPI_E_NO_SUPPORT 
  
> The object does not support named properties. 
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded overall, but names for one or more properties could not be returned. The property tags for the failing properties have a property type of **PT_ERROR**. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md). 
    
MAPI_E_INVALID_PARAMETER 
  
> The **cValues** member of one or more of the entries in the property tag array pointed to by  _lppPropTags_ is set to 0. 
    
## Remarks

While access to most properties is by property identifier, some properties can be accessed by name. The **IMAPIProp::GetNamesFromIDs** method can be called to do the following: 
  
- Retrieve names for specific property identifiers in a specific property set.
    
- Retrieve names for specific property identifiers in any property set.
    
- Retrieve names for all named properties that are included in the object's mapping.
    
If  _lppPropTags_ points to a valid property tag array with one or more property identifiers, and  _lpPropSetGuid_ points to a valid property set, **GetNamesFromIDs** ignores the property set and the property types and returns all of the names that map to the specified identifiers. 
  
If  _lppPropTags_ points to a valid property tag array with one or more property identifiers and  _lpPropSetGuid_ is NULL, **GetNamesFromIDs** returns all of the names that map to the specified identifiers. 
  
If a specified identifier does not have a name, **GetNamesFromIDs** returns NULL in that identifier's place in the structure returned in  _lpppPropNames_ and also returns MAPI_W_ERRORS_RETURNED. 
  
If both  _lpPropSetGuid_ and  _lppPropTags_ are NULL, **GetNamesFromIDs** allocates a new property tag array and returns all of the names for all of the named properties for the object. 
  
When there are no names to be returned, perhaps because there are no properties in the requested property set or all of the properties are of a type excluded by the flags, **GetNamesFromIDs** does the following: 
  
- Returns S_OK.
    
- Allocates a new **SPropTagArray** structure, setting the **cValues** member to 0. 
    
- Sets the contents of  _lpcPropNames_ to 0. 
    
- Sets the contents of  _lpppPropNames_ to NULL. 
    
## Notes to implementers

If  _lpPropSetGuid_ points to a valid property set and  _lppPropTags_ is NULL, the result is undefined. You can use one of the following strategies: 
  
- Ignore the property set and return the names for the identifiers in the property tag array.
    
- Return the names for only the identifiers in the property tag array that belong to the specified property set.
    
- Fail the call, returning MAPI_E_INVALID_PARAMETER. 
    
## Notes to callers

To retrieve all of the named properties for an object, you must first call the object's [IMAPIProp::GetPropList](imapiprop-getproplist.md) method and then pass the returned identifiers that are above the 0x8000 range to **GetNamesFromIDs**.
  
If you pass a valid property set but not a valid property tag array, be prepared for unpredictable results. Some implementations of **GetNamesFromIDs** ignore the property set and return the names for the identifiers in the property tag array. Some implementations return MAPI_E_INVALID_PARAMETER. Still other implementations return names for identifiers of all properties in the property set. If the property set is PS_PUBLIC_STRINGS, **GetNamesFromIDs** can return all names that were ever created. Whether the service provider stores a property under the identifiers associated with the public strings is immaterial. 
  
When you are finished with the property names, check the contents of the  _lpcPropNames_ parameter to determine whether any names were returned. If so, call the [MAPIFreeBuffer](mapifreebuffer.md) function to free the memory pointed to by  _lppPropTags_ and  _lpppPropNames_ when a successful result is returned. One call to **MAPIFreeBuffer** is sufficient for each parameter; you do not have to traverse the array of pointers and free each **MAPINAMEID** structure individually. 
  
For more information about named properties, see [MAPI Named Properties](mapi-named-properties.md). 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|SingleMAPIPropListCtrl.cpp  <br/> |CSingleMAPIPropListCtrl::FindAllNamedProps  <br/> |MFCMAPI uses the **IMAPIProp::GetNamesFromIDs** method to look up named properties that have previously been mapped. |
   
## See also



[GUID](guid.md)
  
[IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md)
  
[IMAPIProp::GetPropList](imapiprop-getproplist.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[MAPINAMEID](mapinameid.md)
  
[SPropTagArray](sproptagarray.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Named Properties](mapi-named-properties.md)
  
[Using Macros for Error Handling](using-macros-for-error-handling.md)

