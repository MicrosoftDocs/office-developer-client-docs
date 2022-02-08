---
title: "IMAPIPropCopyProps"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProp.CopyProps
api_type:
- COM
ms.assetid: f65da1c8-d49b-44e8-8c66-9c53d088d334
description: "Last modified: March 09, 2015"
---

# IMAPIProp::CopyProps

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies or moves selected properties. 
  
```cpp
HRESULT CopyProps(
  LPSPropTagArray lpIncludeProps,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  LPCIID lpInterface,
  LPVOID lpDestObj,
  ULONG ulFlags,
  LPSPropProblemArray FAR * lppProblems
);
```

## Parameters

 _lpIncludeProps_
  
> [in] A pointer to a property tag array that specifies the properties to copy or move. **PR_NULL** ([PidTagNull](pidtagnull-canonical-property.md)) cannot be included in the array. The  _lpIncludeProps_ parameter cannot be **null**.
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. 
    
 _lpProgress_
  
> [in] A pointer to an implementation of a progress indicator. If **null** is passed in the _lpProgress_ parameter, the progress indicator is displayed by using the MAPI implementation. The  _lpProgress_ parameter is ignored unless the MAPI_DIALOG flag is set in the _ulFlags_ parameter. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface that must be used to access the object pointed to by the  _lpDestObj_ parameter. The  _lpInterface_ parameter must not be **null**.
    
 _lpDestObj_
  
> [in] A pointer to the object to receive the copied or moved properties.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the copy or move operation. The following flags can be set:
    
MAPI_DECLINE_OK 
  
> If **CopyProps** calls the [IMAPISupport::DoCopyProps](imapisupport-docopyprops.md) method to handle the copy or move operation, it should instead return immediately with the error value MAPI_E_DECLINE_COPY. The MAPI_DECLINE_OK flag is set by MAPI to limit recursion. Clients do not set this flag. 
    
MAPI_DIALOG 
  
> Displays a progress indicator.
    
MAPI_MOVE 
  
> **CopyProps** should perform a move operation instead of a copy operation. When this flag is not set, **CopyProps** performs a copy operation. 
    
MAPI_NOREPLACE 
  
> Existing properties in the destination object should not be overwritten. When this flag is not set, **CopyProps** overwrites existing properties. 
    
 _lppProblems_
  
> [in, out] On input, a pointer to a pointer to an [SPropProblemArray](spropproblemarray.md) structure; otherwise, **null**, indicating that there is no need for error information. If  _lppProblems_ is a valid pointer on input, **CopyProps** returns detailed information about errors in copying one or more properties. 
    
## Return value

S_OK 
  
> Properties have been successfully copied or moved.
    
MAPI_E_COLLISION 
  
> A subobject cannot be copied because a subobject with the same display name, defined by the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property, already exists in the destination object. 
    
MAPI_E_DECLINE_COPY 
  
> The service provider does not implement the copy operation.
    
MAPI_E_FOLDER_CYCLE 
  
> The source object performing the copy or move operation directly or indirectly contains the destination object. Significant work might have been performed before this condition was discovered, so the source and destination objects might be partially modified. 
    
MAPI_E_INTERFACE_NOT_SUPPORTED 
  
> The interface identified by the  _lpInterface_ parameter is not supported by the destination object. 
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to access an object for which the caller has insufficient permissions. This error is returned if the destination object is the same as the source object.
    
The following values can be returned in the **SPropProblemArray** structure, but not as return values for **CopyProps**. These errors apply to a single property.
  
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and **CopyProps** does not support Unicode, or MAPI_UNICODE was not set and **CopyProps** supports only Unicode. 
    
MAPI_E_COMPUTED 
  
> The property cannot be modified by the caller because it is a read-only property, computed by the owner of the destination object. This error is not severe; the caller should allow the copy operation to continue.
    
MAPI_E_INVALID_TYPE 
  
> The property type is invalid.
    
MAPI_E_UNEXPECTED_TYPE 
  
> The property type is not the type expected by the caller.
    
## Remarks

The **IMAPIProp::CopyProps** method copies or moves selected properties from the current object to a destination object. **CopyProps** is used mainly for replying to and forwarding messages, where only some of the properties from the original message travel with the reply or forwarded copy. 
  
Any subobjects in the source object are automatically included in the operation and copied or moved in their entirety, regardless of the use of properties indicated by the [SPropTagArray](sproptagarray.md) structure. By default, **CopyProps** overwrites any properties in the destination object that match properties from the source object. If any of the copied or moved properties already exist in the destination object, the existing properties are overwritten by the new properties, unless the MAPI_NOREPLACE flag is set in the _ulFlags_ parameter. Existing information in the destination object that is not overwritten is left untouched. 
  
## Notes to implementers

You can provide a full implementation of **CopyProps** or rely on the implementation that MAPI provides in its support object. If you want to use the MAPI implementation, call the **IMAPISupport::DoCopyProps** method. However, if you do delegate processing to **DoCopyProps** and you are passed the MAPI_DECLINE_OK flag, avoid the support call and return MAPI_E_DECLINE_COPY instead. You will be called with this flag by MAPI to avoid the possible recursion that can occur when you copy folders. 
  
Because the copy operation can be lengthy, you should display a progress indicator. Use the [IMAPIProgress](imapiprogressiunknown.md) implementation that is passed in the _lpProgress_ parameter, if there is one. If  _lpProgress_ is **null**, call the [IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md) method to use the MAPI implementation. 
  
## Notes to callers

Do not set the MAPI_DECLINE_OK flag; it is used by MAPI in its calls to message store provider **CopyProps** implementations. 
  
Because copy and move operations can take time, it is wise to request the display of a progress indicator by setting the MAPI_DIALOG flag. You can set the  _lpProgress_ parameter to your implementation of **IMAPIProgress**, if you have one, or to **null**. If  _lpProgress_ is **null**, **CopyProps** will use the default progress indicator provided by MAPI. 
  
You can suppress the display of a progress indicator by not setting the MAPI_DIALOG flag. **CopyProps** will ignore the  _ulUIParam_ and  _lpProgress_ parameters and avoid displaying the indicator. 
  
 **CopyProps** can report global and individual errors, or errors that occur with one or more of the properties. These individual errors are put in an **SPropProblemArray** structure. You can suppress error reporting at the property level by passing **null**, instead of a valid pointer, for the property problem array structure parameter. 
  
If you want to receive information about errors, pass a valid **SPropProblemArray** structure pointer in the _lppProblems_ parameter. When **CopyProps** returns S_OK, check for possible errors with individual properties in the structure. When **CopyProps** returns an error, no information is returned in the **SPropProblemArray** structure. Instead, call the [IMAPIProp::GetLastError](imapiprop-getlasterror.md) method to retrieve detailed error information. 
  
If **CopyProps** returns S_OK, free the returned **SPropProblemArray** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
If you are copying properties that are unique to the source object type, you must make sure that the destination object is of the same type. **CopyProps** does not prevent you from associating properties that typically belong to one type of object with another type of object. It is up to you to copy properties that make sense for the destination object. For example, you should not copy message properties to an address book container. 
  
To ensure that you are copying between objects of the same type, check that the source and destination object are the same type, either by comparing object pointers or calling the [IUnknown::QueryInterface](https://msdn.microsoft.com/library/54d5ff80-18db-43f2-b636-f93ac053146d%28Office.15%29.aspx) method. Set the interface identifier pointed to by  _lpInterface_ to the standard interface for the source object. Also, ensure that the object type or **PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md)) property is the same for the two objects. For example, if you are copying from a message, set  _lpInterface_ to IID_IMessage and the **PR_OBJECT_TYPE** for both objects to MAPI_MESSAGE. 
  
If an invalid pointer is passed in the _lpDestObj_ parameter, the results are unpredictable. 
  
To copy a message's recipient list, call the message's **CopyProps** method and include the **PR_MESSAGE_RECIPIENTS** ([PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) property in the property tag array. To copy the message's attachments, include the **PR_MESSAGE_ATTACHMENTS** ([PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) property. 
  
To copy a folder or address book container's hierarchy or contents table, include the **PR_CONTAINER_HIERARCHY** ([PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md)) or **PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md)) properties in the property tag array. To include a folder's associated contents table, include the **PR_FOLDER_ASSOCIATED_CONTENTS** ([PidTagFolderAssociatedContents](pidtagfolderassociatedcontents-canonical-property.md)) property in the array. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |CopyNamedProps  <br/> |MFCMAPI uses the **IMAPIProp::CopyProps** method to copy named properties from one message to another.  <br/> |
|SingleMAPIPropListCtrl.cpp  <br/> |CSingleMAPIPropListCtrl::OnPasteProperty  <br/> |MFCMAPI uses the **IMAPIProp::CopyProps** method to paste a property that has been copied from another object.  <br/> |
   
## See also



[IMAPIFolder::CopyMessages](imapifolder-copymessages.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)
  
[IMAPIProp::CopyTo](imapiprop-copyto.md)
  
[IMAPIProp::GetLastError](imapiprop-getlasterror.md)
  
[IMAPISupport::DoCopyProps](imapisupport-docopyprops.md)
  
[IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[PidTagContainerContents Canonical Property](pidtagcontainercontents-canonical-property.md)
  
[PidTagContainerHierarchy Canonical Property](pidtagcontainerhierarchy-canonical-property.md)
  
[PidTagDisplayName Canonical Property](pidtagdisplayname-canonical-property.md)
  
[PidTagFolderAssociatedContents Canonical Property](pidtagfolderassociatedcontents-canonical-property.md)
  
[PidTagMessageAttachments Canonical Property](pidtagmessageattachments-canonical-property.md)
  
[PidTagMessageRecipients Canonical Property](pidtagmessagerecipients-canonical-property.md)
  
[PidTagObjectType Canonical Property](pidtagobjecttype-canonical-property.md)
  
[SPropProblemArray](spropproblemarray.md)
  
[SPropTagArray](sproptagarray.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

