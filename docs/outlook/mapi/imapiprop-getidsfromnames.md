---
title: "IMAPIPropGetIDsFromNames"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProp.GetIDsFromNames
api_type:
- COM
ms.assetid: e3f501a4-a8ee-43d7-bd83-c94e7980c398
description: "Last modified: March 09, 2015"
---

# IMAPIProp::GetIDsFromNames

  
  
**Applies to**: Outlook 
  
Provides the property identifiers that correspond to one or more property names.
  
```cpp
HRESULT GetIDsFromNames(
  ULONG cPropNames,
  LPMAPINAMEID FAR * lppPropNames,
  ULONG ulFlags,
  LPSPropTagArray FAR * lppPropTags
);
```

## Parameters

 _cPropNames_
  
> [in] The count of property names pointed to by the  _lppPropNames_ parameter. If  _lppPropNames_ is NULL, the  _cPropNames_ parameter must be 0. 
    
 _lppPropNames_
  
> [in] A pointer to an array of property names, or NULL. Passing NULL requests property identifiers for all property names in all property sets about which the object has information. The  _lppPropNames_ parameter must not be NULL if the MAPI_CREATE flag is set in the  _ulFlags_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that indicates how the property identifiers should be returned. The following flag can be set:
    
MAPI_CREATE 
  
> Assigns a property identifier, if one has not yet been assigned, to one or more of the names included in the property name array pointed to by  _lppPropNames_. This flag internally registers the identifier in the name-to-identifier mapping table.
    
 _lppPropTags_
  
> [out] A pointer to a pointer to an array of property tags that contains existing or newly assigned property identifiers. The property types for the property tags in this array are set to **PT_UNSPECIFIED**.
    
## Return value

S_OK 
  
> The identifiers for the specified property names were successfully returned.
    
MAPI_E_NO_SUPPORT 
  
> The object does not support named properties.
    
MAPI_E_NOT_ENOUGH_MEMORY 
  
> Insufficient memory was available to retrieve the identifiers.
    
MAPI_E_TOO_BIG 
  
> The operation cannot be performed because it requires too many property tags to be returned.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded overall, but one or more property identifiers could not be returned. The corresponding property type for each unavailable property is set to **PT_ERROR** and its identifier to zero. When this warning is returned, handle the call as successful. To test for this warning, use the **HR_FAILED** macro. See [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPIProp::GetIDsFromNames** method retrieves an array of property tags that hold the property identifiers for one or more named properties. **IMAPIProp::GetIDsFromNames** can be called to do the following: 
  
- Create identifiers for new names.
    
- Retrieve identifiers for specific names.
    
- Retrieve identifiers for all named properties that are included in the object's mapping.
    
Named properties are typically used by message store providers for folders and messages. Other objects, such as messaging users and profile sections, might not support the association of names to property identifiers and might return MAPI_E_NO_SUPPORT from **GetIDsFromNames**.
  
If there is an error that returns an identifier for a particular name, **GetIDsFromNames** returns MAPI_W_ERRORS_RETURNED and sets the property type in the property tag array entry that corresponds to the name to **PT_ERROR** and the identifier to zero. 
  
Name-to-identifier mapping is represented by an object's **PR_MAPPING_SIGNATURE** ([PidTagMappingSignature](pidtagmappingsignature-canonical-property.md)) property. **PR_MAPPING_SIGNATURE** contains a [MAPIUID](mapiuid.md) structure that indicates the service provider responsible for the object. If the **PR_MAPPING_SIGNATURE** property is the same for two objects, assume that these objects use the same name-to-identifier mapping. 
  
## Notes to implementers

The identifiers that you pass back in the property tag array pointed to by the  _lppPropNames_ parameter must be in the 0x8000 to 0xFFFE range. The entries in this array must be in the same order as the names passed in the property name array pointed to by  _lppPropNames_. 
  
If you support named properties on a container, use the same name-to-identifier mapping for all objects in your container (that is, do not use a different mapping for each folder in your message store or each message in your folder).
  
## Notes to callers

Because the property types for the returned identifiers in the property tag array pointed to by  _lppPropTags_ are set to **PT_UNSPECIFIED**, you will have to call the [IMAPIProp::SetProps](imapiprop-setprops.md) method to retrieve the accurate types. 
  
If you move or copy objects with named properties, and the source and destination objects have different mapping signatures as indicated by the values of their **PR_MAPPING_SIGNATURE** properties, you must preserve the names during these operations. To preserve property names, adjust the corresponding property identifiers to match the name-to-identifier mapping of the destination object. 
  
Some objects have a limit as to the number of property identifiers they can name. If a call to **GetIDsFromNames** causes this limit to be exceeded, the method returns MAPI_E_TOO_BIG. In this case, query by identifier. 
  
For more information, see [MAPI Named Properties](mapi-named-properties.md). 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|SingleMAPIPropListCtrl.cpp  <br/> |CSingleMAPIPropListCtrl::FindAllNamedPropsUsed  <br/> |MFCMAPI uses the **IMAPIProp::GetIDsFromNames** method to obtain property tags for all named properties that have been mapped.  <br/> |
   
## See also



[IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md)
  
[IMAPIProp::SetProps](imapiprop-setprops.md)
  
[MAPINAMEID](mapinameid.md)
  
[MAPIUID](mapiuid.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Named Properties](mapi-named-properties.md)
  
[Using Macros for Error Handling](using-macros-for-error-handling.md)

