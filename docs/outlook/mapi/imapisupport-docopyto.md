---
title: "IMAPISupportDoCopyTo"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.DoCopyTo
api_type:
- COM
ms.assetid: 84019475-5176-4fc5-a3ee-871095077498
---

# IMAPISupport::DoCopyTo

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies or moves all properties of one object, except for specifically excluded properties, to another object.
  
```cpp
HRESULT DoCopyTo(
  LPCIID lpSrcInterface,
  LPVOID lpSrcObj,
  ULONG ciidExclude,
  LPCIID rgiidExclude,
  LPSPropTagArray lpExcludeProps,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  LPCIID lpDestInterface,
  LPVOID lpDestObj,
  ULONG ulFlags,
  LPSPropProblemArray FAR * lppProblems
);
```

## Parameters

 _lpSrcInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the object that has the properties to be copied or moved.
    
 _lpSrcObj_
  
> [in] A pointer to the object that has the properties to be copied or moved.
    
 _ciidExclude_
  
> [in] The count of interfaces to exclude when you copy or move properties.
    
 _rgiidExclude_
  
> [in] An array of interface identifiers that indicates interfaces that should not be used when you copy or move supplemental information to the destination object.
    
 _lpExcludeProps_
  
> [in] A pointer to a property tag array that identifies the property tags that should be excluded from the copy or move operation. Passing NULL in the _lpExcludeProps_ parameter indicates that all of the object's properties should be copied or moved. **DoCopyTo** returns MAPI_E_INVALID_PARAMETER when the **cValues** member of the [SPropTagArray](sproptagarray.md) structure pointed to by  _lpExcludeProps_ is set to 0. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. 
    
 _lpProgress_
  
> [in] A pointer to a progress indicator implementation. If NULL is passed in the _lpProgress_ parameter, MAPI provides the progress implementation. The  _lpProgress_ parameter is ignored unless the MAPI_DIALOG flag is set in the _ulFlags_ parameter. 
    
 _lpDestInterface_
  
> [in] A pointer to the interface identifier that represents the interface to be used to access the object to receive the copied or moved properties.
    
 _lpDestObj_
  
> [in] A pointer to the object to receive the copied or moved properties.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the copy or move operation. The following flags can be set:
    
MAPI_DIALOG 
  
> Displays a progress indicator. 
    
MAPI_MOVE 
  
> **DoCopyTo** should perform a move operation instead of a copy operation. When this flag is not set, **DoCopyTo** performs a copy operation. 
    
MAPI_NOREPLACE 
  
> Existing properties in the destination object should not be overwritten. When this flag is not set, **DoCopyTo** overwrites existing properties. 
    
 _lppProblems_
  
> [out] On input, a pointer to a pointer to an [SPropProblemArray](spropproblemarray.md) structure; otherwise, NULL, which indicates no need for error information. If  _lppProblems_ is a valid pointer on input, **DoCopyTo** returns detailed information about errors in copying one or more properties. 
    
## Return value

S_OK 
  
> The properties have been successfully copied or moved.
    
MAPI_E_COLLISION 
  
> A property to be copied or moved already exists in the destination object and the MAPI_NOREPLACE flag is set. 
    
MAPI_E_FOLDER_CYCLE 
  
> The source object directly or indirectly contains the destination object. Significant work might have been performed before this condition was discovered, so the source and destination objects might be partially modified. 
    
MAPI_E_INTERFACE_NOT_SUPPORTED 
  
> The interface identified by the  _lpSrcInterface_ parameter is not supported by the object pointed to by  _lpSrcObj_, or the interface identified by the  _lpDestInterface_ parameter is not supported by the object pointed to by  _lpDestObj_. 
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to access an object for which the caller has insufficient permissions. This error is returned if the destination object is the same as the source object.
    
MAPI_E_INVALID_PARAMETER 
  
> The  _lpSrcInterface_ parameter is NULL. 
    
The following values can be returned in the **SPropProblemArray** structure, but not as return values for **DoCopyTo**. These errors apply to a single property.
  
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and **DoCopyTo** does not support Unicode, or MAPI_UNICODE was not set and **DoCopyTo** supports only Unicode. 
    
MAPI_E_COMPUTED 
  
> The property cannot be modified by the caller because it is a read-only property, computed by the owner of the destination object. This error is not severe; the caller should allow the copy operation to continue.
    
MAPI_E_INVALID_TYPE 
  
> The property type is invalid.
    
MAPI_E_UNEXPECTED_TYPE 
  
> The property type is not the type expected by the caller.
    
## Remarks

The **IMAPISupport::DoCopyTo** method is implemented for message store provider support objects. Message store providers can call **DoCopyTo** to implement the [IMAPIProp::CopyTo](imapiprop-copyto.md) method for their folders and messages. 
  
By default, **DoCopyTo** copies or moves all of the properties of one object to another object. Any subobjects in the source object are automatically included in the operation and copied or moved in their entirety. 
  
If any of the copied or moved properties already exist in the destination object, the existing properties are overwritten by the new properties, unless the MAPI_NOREPLACE flag is set in the _ulFlags_ parameter. Existing information in the destination object that is not overwritten is left untouched. 
  
## Notes to callers

To exclude properties from the copy or move operation, include their property tags in the _lpExcludeProps_ parameter. If you pass the results of using the [PROP_TAG](prop_tag.md) macro to build a property tag from a specific identifier in the property tag array, all properties with that identifier will be excluded. For example, the following entry in the property tag array causes all properties with an identifier of 0x8002 to be excluded, regardless of type: 
  
 `PROP_TAG(PT_LONG, 0x8002)`
  
To avoid copying a message's delivery time when you copy the message to a different folder, specify **PR_MESSAGE_DELIVERY_TIME** ([PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md)) in the property tag exclude array. To exclude a message's recipient list, add the **PR_MESSAGE_RECIPIENTS** ([PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) property to the exclude array. To exclude a message's attachments, add the **PR_MESSAGE_ATTACHMENTS** ([PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) property to the array.
  
Similarly, to prevent the copying or moving of a folder or address book container's hierarchy or contents table, include **PR_CONTAINER_HIERARCHY** ([PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md)) or **PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md)) in the property tag exclude array.
  
Ignore MAPI_E_COMPUTED errors returned in the **SPropProblemArray** structure in the _lppProblems_ parameter. 
  
The interface identifier that  _lpSrcInterface_ points to is usually the same as the interface identifier that  _lpDestInterface_ points to. 
  
If you pass an acceptable interface identifier in  _lpDestInterface_ but an invalid pointer in  _lpDestObj_, the results are unpredictable. Most likely this will cause your provider to fail. 
  
Conversely, if you are aware of supplemental information that should not be copied or moved, add the interface identifiers for the interfaces to be excluded in the array passed in the _rgiidExclude_ parameter. For example, if you are copying messages, but not any of their message attachments, pass IID_IMessage in the _rgiidExclude_ array. **DoCopyTo** ignores any interfaces listed in  _rgiidExclude_ that it does not recognize. 
  
When you use the  _rgiidExclude_ parameter to exclude an interface, it also excludes all interfaces derived from that interface. For example, excluding the [IMAPIContainer](imapicontainerimapiprop.md) interface causes folders or address book containers to be excluded, depending on the type of provider. Do not exclude [IMAPIProp](imapipropiunknown.md) or [IUnknown](https://msdn.microsoft.com/library/33f1d79a-33fc-4ce5-a372-e08bda378332%28Office.15%29.aspx) because so many interfaces derive from them. 
  
 **DoCopyTo** reports global errors that apply to the operation as a whole, and individual errors that apply to individual properties. These individual errors are put in an **SPropProblemArray** structure. You can suppress error reporting at the property level by passing NULL, rather than a valid pointer, for the property problem array structure parameter. 
  
If you want to receive information about errors, pass a valid **SPropProblemArray** structure pointer in the _lppProblems_ parameter. When **DoCopyTo** returns S_OK, check for possible errors with individual properties in the structure. When **DoCopyTo** returns an error, no information is returned in the **SPropProblemArray** structure. Instead, call the [IMAPISupport::GetLastError](imapisupport-getlasterror.md) method to retrieve detailed error information. 
  
If **DoCopyTo** returns S_OK, free the returned **SPropProblemArray** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
If a global error occurs on the **DoCopyTo** call, do not use or free the **SPropProblemArray** structure. Providers should ignore the  _ulIndex_ member in **SPropProblemArray** structures returned by **DoCopyTo**.
  
## See also



[IMAPIProp::CopyTo](imapiprop-copyto.md)
  
[IMAPISupport::CopyFolder](imapisupport-copyfolder.md)
  
[IMAPISupport::CopyMessages](imapisupport-copymessages.md)
  
[IMAPISupport::GetLastError](imapisupport-getlasterror.md)
  
[PidTagContainerContents Canonical Property](pidtagcontainercontents-canonical-property.md)
  
[PidTagContainerHierarchy Canonical Property](pidtagcontainerhierarchy-canonical-property.md)
  
[PidTagMessageAttachments Canonical Property](pidtagmessageattachments-canonical-property.md)
  
[PidTagMessageDeliveryTime Canonical Property](pidtagmessagedeliverytime-canonical-property.md)
  
[PidTagMessageRecipients Canonical Property](pidtagmessagerecipients-canonical-property.md)
  
[SPropProblemArray](spropproblemarray.md)
  
[SPropTagArray](sproptagarray.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

