---
title: "IMAPIPropGetProps"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProp.GetProps
api_type:
- COM
ms.assetid: 1c7a9cd2-d765-4218-9aee-52df1a2aae6c
description: "Last modified: March 09, 2015"
---

# IMAPIProp::GetProps

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the property value of one or more properties of an object.
  
```cpp
HRESULT GetProps(
  LPSPropTagArray lpPropTagArray,
  ULONG ulFlags,
  ULONG FAR * lpcValues,
  LPSPropValue FAR * lppPropArray
);
```

## Parameters

 _lpPropTagArray_
  
> [in] A pointer to an array of property tags that identify the properties whose values are to be retrieved. The  _lpPropTagArray_ parameter must be either NULL, indicating that values for all properties of the object should be returned, or point to an [SPropTagArray](sproptagarray.md) structure that contains one or more property tags. 
    
 _ulFlags_
  
> [in] A bitmask of flags that indicates the format for properties that have the type PT_UNSPECIFIED. The following flag can be set:
    
MAPI_UNICODE 
  
> The string values for these properties should be returned in the Unicode format. If the MAPI_UNICODE flag is not set, the string values should be returned in the ANSI format.
    
 _lpcValues_
  
> [out] A pointer to a count of property values pointed to by the  _lppPropArray_ parameter. If  _lppPropArray_ is NULL, the content of the  _lpcValues_ parameter is zero. 
    
 _lppPropArray_
  
> [out] A pointer to a pointer to the retrieved property values.
    
## Return value

S_OK 
  
> The property values were successfully retrieved.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded overall, but one or more properties could not be accessed. The **aulPropTag** member of the property value for each unavailable property has a property type of PT_ERROR and an identifier of zero. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
MAPI_E_INVALID_PARAMETER 
  
> Zero was passed in the **cValues** member of the **SPropTagArray** structure pointed to by  _lpPropTagArray_.
    
## Remarks

The **IMAPIProp::GetProps** method obtains the property values of one or more properties of an object. 
  
The property values are returned in the same order as they were requested (that is, the order of properties in the property tag array pointed to by  _lpPropTagArray_ matches the order in the array of property value structures pointed to by  _lppPropArray_). 
  
The property types specified in the **aulPropTag** members of the property tag array indicate the type of value that should be returned in the **Value** member of each property value structure. However, if the caller does not know the type of a property, the type in the **aulPropTag** member can be set instead to PT_UNSPECIFIED. In retrieving the value, **GetProps** sets the correct type in the **aulPropTag** member of the property value structure for the property. 
  
If property types are specified in the **SPropTagArray** in  _lpPropTagArray_, the property values in the **SPropValue** returned in  _lppPropArray_ have types that exactly match the requested types, unless an error value is returned instead. 
  
String properties can have one of two property types: PT_UNICODE to represent the Unicode format and PT_STRING8 to represent the ANSI format. If the MAPI_UNICODE flag is set in the  _ulFlags_ parameter, whenever **GetProps** cannot determine the appropriate format for a string property, it returns its value in the Unicode format. **GetProps** cannot determine an exact string property type in the following situations: 
  
- The  _lpPropTagArray_ parameter is set to NULL to request all properties. 
    
- The **aulPropTag** member includes the value PT_UNSPECIFIED as its property type in the property tag array. 
    
If the  _lpPropTagArray_ parameter is set to NULL to retrieve all of the properties of the object and no properties exist, **GetProps** does the following: 
  
- Returns S_OK.
    
- Sets the count value in the **cValues** member of the property value structure to 0. 
    
- Sets the contents of  _lpcValues_ to 0. 
    
- Sets  _lppPropArray_ to NULL. 
    
 **GetProps** must not return multiple-value properties with **cValues** set to 0. 
  
## Notes to implementers

Call the [MAPIAllocateBuffer](mapiallocatebuffer.md) function to allocate memory initially for the [SPropValue](spropvalue.md) structure pointed to by  _lpPropTagArray_; call [MAPIAllocateMore](mapiallocatemore.md) to allocate any additional memory needed for the structure's members. 
  
Return MAPI_W_ERRORS_RETURNED if you cannot retrieve the value for one or more of the requested properties. In the property value structure, set the type in the **aulPropTag** member to PT_ERROR and the **Value** member to a status code that describes the error. For example, if you have to convert a string to Unicode and do not support Unicode, set the **Value** member to MAPI_E_BAD_CHARWIDTH. If the property is too large, set it to MAPI_E_NOT_ENOUGH_MEMORY. If the object does not support the property, set it to MAPI_E_NOT_FOUND. 
  
A remote transport provider's implementation of the **GetProps** method must return the folder's property values for properties requested by the caller. Your implementation must do the following: 
  
- Allocate a property value array to return to the caller and store its address in the property value pointer parameter passed in for that purpose.
    
- Copy the property tags from the folder's properties into the property tags in the property value array according to the array of property tags passed to **GetProps**.
    
- Ensure that the property type is set for all property tags passed to **GetProps**. The caller can pass in a property type of PT_UNSPECIFIED, in which case **GetProps** must set the correct property type for that property tag. 
    
- Set the value of each property in the property value array according to its tag. For example, if the property tag requested by the caller is **PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md)), **GetProps** can set the value to MAPI_FOLDER. 
    
- If the caller passes in any property tags that your implementation does not handle, you can set the property tag to PT_ERROR for those properties, and set the property value to MAPI_E_NOT_FOUND.
    
- Return S_OK if no errors occurred or MAPI_W_ERRORS_RETURNED if there were errors.
    
A remote transport provider's implementation of the **GetProps** method must support the following properties at a minimum: 
  
- **PR_ACCESS** ([PidTagAccess](pidtagaccess-canonical-property.md))
    
- **PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md))
    
- **PR_ASSOC_CONTENT_COUNT** ([PidTagAssociatedContentCount](pidtagassociatedcontentcount-canonical-property.md))
    
- **PR_CONTENT_COUNT** ([PidTagContentCount](pidtagcontentcount-canonical-property.md))
    
- **PR_CREATION_TIME** ([PidTagCreationTime](pidtagcreationtime-canonical-property.md))
    
- **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
- **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))
    
- **PR_FOLDER_TYPE** ([PidTagFolderType](pidtagfoldertype-canonical-property.md))
    
- **PR_OBJECT_TYPE**
    
- **PR_SUBFOLDERS** ([PidTagSubfolders](pidtagsubfolders-canonical-property.md))
    
## Notes to callers

For properties of type PT_OBJECT, call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method instead of **GetProps**. 
  
For secure properties, do not expect to retrieve them by calling **GetProps** with the  _lppPropTagArray_ parameter set to NULL. You must explicitly set a secure property's identifier in the **aulPropTag** member of its property tag array when you call **GetProps**. When and how a secure property is available is up to the service provider. 
  
Free the returned **SPropValue** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function only if **GetProps** returns S_OK or MAPI_W_ERRORS_RETURNED. 
  
If **GetProps** returns MAPI_W_ERRORS_RETURNED because it could not access one or more properties, check the property tags of the returned properties. The failed properties will have the following values set in their property value structure: 
  
- The property type in the **aulPropTag** member set to PT_ERROR. 
    
- The property value in the **Value** member set to a status code for the error, such as MAPI_E_NOT_FOUND. 
    
Properties that fail because they are too large to conveniently be returned in the property value structure have their **Value** member set to MAPI_E_NOT_ENOUGH_MEMORY. Typically, this occurs with string or binary properties of type PT_STRING8, PT_UNICODE, or PT_BINARY when the value of the property is 4 KB or larger. Call **IMAPIProp::OpenProperty** to retrieve large properties. 
  
Not all implementations of **GetProps** support both the Unicode and ANSI formats for character strings. When a particular property requires string format conversion and **GetProps** cannot support it, the **Value** member for the property is set to MAPI_E_BAD_CHARWIDTH. 
  
To check if a PST is a SharePoint PST, mount the PST using [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md), then call **GetProps** on the message store object requesting this property. If it exists, you can assume the PST has been configured for SharePoint; if not, the PST has not been configured as a SharePoint PST. 
  
For more information about how to use **GetProps** to access properties, see [Retrieving MAPI Properties](retrieving-mapi-properties.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |GetPropsNULL  <br/> |MFCMAPI uses the **IMAPIProp::GetProps** method to obtain all properties for an object by passing either NULL or the array returned by the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method in the  _lpPropTagArray_ parameter.  <br/> |
   
## See also



[IMAPIProp::GetPropList](imapiprop-getproplist.md)
  
[IMAPIProp::OpenProperty](imapiprop-openproperty.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIAllocateMore](mapiallocatemore.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropTagArray](sproptagarray.md)
  
[SPropValue](spropvalue.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Retrieving MAPI Properties](retrieving-mapi-properties.md)
  
[Using Macros for Error Handling](using-macros-for-error-handling.md)

