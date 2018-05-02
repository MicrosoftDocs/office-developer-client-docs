---
title: "IMAPISupportDoCopyProps"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.DoCopyProps
api_type:
- COM
ms.assetid: 2446ef52-578a-4004-9719-de9b0207ccad
description: "Last modified: July 23, 2011"
---

# IMAPISupport::DoCopyProps

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Copies or moves one or more properties of an object to another object.
  
```
HRESULT DoCopyProps(
  LPCIID lpSrcInterface,
  LPVOID lpSrcObj,
  LPSPropTagArray lpIncludeProps,
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
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the object with the properties to be copied or moved.
    
 _lpSrcObj_
  
> [in] A pointer to the object that contains the properties to be copied or moved.
    
 _lpIncludeProps_
  
> [in] A pointer to an [SPropTagArray](sproptagarray.md) structure that contains a counted array of property tags that indicate the properties to copy or move. The  _lpIncludeProps_ parameter cannot be NULL. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator.
    
 _lpProgress_
  
> [in] A pointer to an implementation of a progress indicator. If NULL is passed in the  _lpProgress_ parameter, the progress indicator is displayed by using the MAPI implementation. The  _lpProgress_ parameter is ignored unless the MAPI_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _lpDestInterface_
  
> [in] A pointer to the interface identifier that represents the interface to be used to access the object to receive the properties that are copied or moved.
    
 _lpDestObj_
  
> [in] A pointer to the object to receive the copied or moved properties.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the copy or move operation is performed. The following flags can be set:
    
MAPI_DIALOG 
  
> Displays a progress indicator.
    
MAPI_MOVE 
  
> **DoCopyProps** should perform a move operation instead of a copy operation. When this flag is not set, **DoCopyProps** performs a copy operation. 
    
MAPI_NOREPLACE 
  
> Existing properties in the destination object should not be overwritten. When this flag is not set, **DoCopyProps** overwrites existing properties. 
    
 _lppProblems_
  
> [in, out] On input, a pointer to a pointer to an [SPropProblemArray](spropproblemarray.md) structure; otherwise, NULL, which indicates no need for error information. If  _lppProblems_ is a valid pointer on input, **DoCopyProps** returns detailed information about errors in copying one or more properties. 
    
## Return value

S_OK 
  
> Properties were successfully copied or moved.
    
MAPI_E_COLLISION 
  
> A property to be copied or moved already exists in the destination object and the MAPI_NOREPLACE flag is set. 
    
MAPI_E_FOLDER_CYCLE 
  
> The source object directly or indirectly contains the destination object. Significant work might have been performed before this condition was discovered, so the source and destination objects might be partially modified. 
    
MAPI_E_INTERFACE_NOT_SUPPORTED 
  
> The interface identified by the  _lpSrcInterface_ parameter is not supported by the source object, or the interface identified by the  _lpDestInterface_ parameter is not supported by the destination object. 
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to access an object for which the caller has insufficient permissions. This error is returned if the destination object is the same as the source object.
    
The following values can be returned in the **SPropProblemArray** structure, but not as return values for **DoCopyProps**. These errors apply to a single property.
  
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and **DoCopyProps** does not support Unicode, or MAPI_UNICODE was not set and **DoCopyProps** supports only Unicode. 
    
MAPI_E_COMPUTED 
  
> The property cannot be modified by the caller because it is a read-only property, computed by the owner of the destination object. This error is not severe; the caller should allow the copy operation to continue.
    
MAPI_E_INVALID_TYPE 
  
> The property type is invalid.
    
MAPI_E_UNEXPECTED_TYPE 
  
> The property type is not the type that the caller expects.
    
## Remarks

The **IMAPISupport::DoCopyProps** method is implemented for message store provider support objects. Message store providers can call **DoCopyProps** to implement the [IMAPIProp::CopyProps](imapiprop-copyprops.md) method for their folders and messages. **DoCopyProps** copies or moves the properties that are identified in the property tag array pointed to by  _lpIncludeProps_ and that are present in the object pointed to by  _lpSrcObj_. 
  
## Notes to Callers

When you copy properties between objects of the same type, such as two messages, the  _lpSrcInterface_ and  _lpDestInterface_ parameters must contain the same interface identifier, and the  _lpSrcObj_ and  _lpDestObj_ parameters must point to objects of the same type. If  _lpDestInterface_ is set to NULL, **DoCopyProps** returns MAPI_E_INVALID_PARAMETER. If you set  _lpDestInterface_ to an acceptable interface identifier, but set  _lpDestObj_ to an invalid pointer, the results are unpredictable. Most likely your provider will fail. 
  
Set the MAPI_NOREPLACE flag if you do not want any of the properties in the destination object to be overwritten. Properties in the destination object that exist in the source object and are not overwritten are not deleted or modified.
  
To copy a message's recipient list, include the **PR_MESSAGE_RECIPIENTS** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) property in the property tag array pointed to by the  _lpIncludeProps_ parameter. To copy the message's attachments, include the **PR_MESSAGE_ATTACHMENTS** ( [PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) property. 
  
To copy a folder or address book container's hierarchy or contents table, include **PR_CONTAINER_HIERARCHY** ( [PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md)) or **PR_CONTAINER_CONTENTS** ( [PidTagContainerContents](pidtagcontainercontents-canonical-property.md)) in the property tag array. To include a folder's associated contents table, include the **PR_FOLDER_ASSOCIATED_CONTENTS** ( [PidTagFolderAssociatedContents](pidtagfolderassociatedcontents-canonical-property.md)) property in the array.
  
If subfolders are copied or moved, their contents are copied or moved in their entirety, regardless of the use of properties indicated by the **SPropTagArray** structure. 
  
 **DoCopyProps** reports global errors that occur with the operation as a whole, and individual errors that occur with one or more of the properties. These individual errors are put in an **SPropProblemArray** structure. You can suppress error reporting at the property level by passing NULL, rather than a valid pointer, for the property problem array structure parameter. 
  
If you want to receive information about errors, pass a valid **SPropProblemArray** structure pointer in the  _lppProblems_ parameter. When **DoCopyProps** returns S_OK, check for possible errors with individual properties in the structure. When **DoCopyProps** returns an error, no information is returned in the **SPropProblemArray** structure. Instead, call the [IMAPISupport::GetLastError](imapisupport-getlasterror.md) method to retrieve detailed error information. 
  
If **DoCopyProps** returns S_OK, free the returned **SPropProblemArray** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## See also

#### Reference

[IMAPIProp::CopyProps](imapiprop-copyprops.md)
  
[IMAPISupport::CopyMessages](imapisupport-copymessages.md)
  
[IMAPISupport::DoCopyTo](imapisupport-docopyto.md)
  
[IMAPISupport::GetLastError](imapisupport-getlasterror.md)
  
[PidTagContainerContents Canonical Property](pidtagcontainercontents-canonical-property.md)
  
[PidTagContainerHierarchy Canonical Property](pidtagcontainerhierarchy-canonical-property.md)
  
[PidTagFolderAssociatedContents Canonical Property](pidtagfolderassociatedcontents-canonical-property.md)
  
[PidTagMessageAttachments Canonical Property](pidtagmessageattachments-canonical-property.md)
  
[PidTagMessageRecipients Canonical Property](pidtagmessagerecipients-canonical-property.md)
  
[SPropProblemArray](spropproblemarray.md)
  
[SPropTagArray](sproptagarray.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

