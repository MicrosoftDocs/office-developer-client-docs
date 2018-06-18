---
title: "IMAPIPropCopyTo"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProp.CopyTo
api_type:
- COM
ms.assetid: e56042e9-5bb7-4a99-b6de-1546d4ca07f0
description: "Last modified: March 09, 2015"
---

# IMAPIProp::CopyTo

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies or moves all properties, except for specifically excluded properties.
  
```cpp
HRESULT CopyTo(
 ULONG ciidExclude,
 LPCIID rgiidExclude,
 LPSPropTagArray lpExcludeProps,
 ULONG_PTR ulUIParam,
 LPMAPIPROGRESS lpProgress,
 LPCIID lpInterface,
 LPVOID lpDestObj,
 ULONG ulFlags,
 LPSPropProblemArray FAR * lppProblems
);
```

## Parameters

 _ciidExclude_
  
> [in] The count of interfaces to exclude when properties are copied or moved.
    
 _rgiidExclude_
  
> [in] An array of interface identifiers (IIDs) that specify interfaces that should not be used when supplemental information is copied or moved to the destination object.
    
 _lpExcludeProps_
  
> [in] A pointer to a property tag array that identifies the property tags that should be excluded from the copy or move operation. Passing **null** in the  _lpExcludeProps_ parameter indicates that all of the object's properties should be copied or moved. **CopyTo** returns MAPI_E_INVALID_PARAMETER when the **cValues** member of the [SPropProblemArray](spropproblemarray.md) structure pointed to by  _lpExcludeProps_ is set to 0. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. 
    
 _lpProgress_
  
> [in] A pointer to a progress indicator implementation. If **null** is passed in the  _lpProgress_ parameter, MAPI provides the progress implementation. The  _lpProgress_ parameter is ignored unless the MAPI_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the object pointed to by the  _lpDestObj_ parameter. The  _lpInterface_ parameter must not be **null**.
    
 _lpDestObj_
  
> [in] A pointer to the object to receive the copied or moved properties.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the copy or move operation. The following flags can be set:
    
MAPI_DECLINE_OK 
  
> If **CopyTo** calls the [IMAPISupport::DoCopyTo](imapisupport-docopyto.md) method to handle the copy or move operation, it should instead return immediately with the error value MAPI_E_DECLINE_COPY. The MAPI_DECLINE_OK flag is set by MAPI to limit recursion. Clients do not set this flag. 
    
MAPI_DIALOG 
  
> Displays a progress indicator.
    
MAPI_MOVE 
  
> **CopyTo** should perform a move operation instead of a copy operation. When this flag is not set, **CopyTo** performs a copy operation. 
    
MAPI_NOREPLACE 
  
> Existing properties in the destination object should not be overwritten. When this flag is not set, **CopyTo** overwrites existing properties. 
    
 _lppProblems_
  
> [in, out] On input, a pointer to a pointer to an **SPropProblemArray** structure; otherwise, **null**, indicating no need for error information. If  _lppProblems_ is a valid pointer on input, **CopyTo** returns detailed information about errors in copying one or more properties. 
    
## Return value

S_OK 
  
> The properties have been successfully copied or moved.
    
MAPI_E_COLLISION 
  
> A subobject cannot be copied because a subobject with the same display name — specified by the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property — already exists in the destination object. 
    
MAPI_E_DECLINE_COPY 
  
> The service provider does not implement the copy operation.
    
MAPI_E_FOLDER_CYCLE 
  
> The source object performing the copy or move operation directly or indirectly contains the destination object. Significant work might have been performed before this condition was discovered, so the source and destination objects might be partially modified. 
    
MAPI_E_INTERFACE_NOT_SUPPORTED 
  
> The interface identified by the  _lpInterface_ parameter is not supported by the destination object. 
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to access an object for which the caller has insufficient permissions. This error is returned if the destination object is the same as the source object.
    
The following values can be returned in the **SPropProblemArray** structure, but not as return values for **CopyTo**. The following errors apply to a single property:
  
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and **CopyTo** does not support Unicode, or MAPI_UNICODE was not set and **CopyTo** supports only Unicode. 
    
MAPI_E_COMPUTED 
  
> The property cannot be modified by the caller because it is a read-only property, computed by the owner of the destination object. This error is not severe; the caller should allow the copy operation to continue.
    
MAPI_E_INVALID_TYPE 
  
> The property type is invalid.
    
MAPI_E_UNEXPECTED_TYPE 
  
> The property type is not the type expected by the caller.
    
## Remarks

By default, the **IMAPIProp::CopyTo** method copies or moves all of the current object's properties to a destination object. **CopyTo** is used when an object should be copied or moved exactly, with all or most of its properties intact. 
  
Any subobjects in the source object are automatically included in the operation and are copied or moved in their entirety. By default, **CopyTo** overwrites any properties in the destination object that match properties from the source object. If any of the copied or moved properties already exist in the destination object, the existing properties are overwritten by the new properties, unless the MAPI_NOREPLACE flag is set in the  _ulFlags_ parameter. Existing information in the destination object that is not overwritten is left untouched. 
  
## Notes to implementers

You can provide a full implementation of **CopyTo** or rely on the implementation that MAPI provides in its support object. If you want to use the MAPI implementation, call **IMAPISupport::DoCopyTo**. However, if you do delegate processing to **DoCopyTo** and you are passed the MAPI_DECLINE_OK flag, avoid the support call and return MAPI_E_DECLINE_COPY instead. MAPI will call with this flag to avoid the possible recursion that can happen when folders are copied. 
  
Because the copy operation can be lengthy, you should display a progress indicator. Use the [IMAPIProgress](imapiprogressiunknown.md) implementation passed in the  _lpProgress_ parameter, if there is one. If  _lpProgress_ is **null**, call the [IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md) method to use the MAPI implementation. 
  
Do not attempt to set any known read-only properties in the destination object; return MAPI_E_NO_ACCESS instead.
  
The source and destination objects should use the same interfaces. Return MAPI_E_INVALID_PARAMETER if  _lpInterface_ is not set. 
  
Return MAPI_E_INTERFACE_NOT_SUPPORTED if all known interfaces are excluded.
  
## Notes to callers

Do not set the MAPI_DECLINE_OK flag; MAPI uses it in its calls to message store provider **CopyTo** implementations. 
  
Because copy and move operations can take time, you should request the display of a progress indicator by setting the MAPI_DIALOG flag. You can set the  _lpProgress_ parameter to your implementation of **IMAPIProgress**, if you have one, or to **null**. If  _lpProgress_ is **null**, **CopyTo** will use the default progress indicator that MAPI provides. 
  
You can suppress the display of a progress indicator by not setting the MAPI_DIALOG flag. **CopyTo** will ignore the  _ulUIParam_ and  _lpProgress_ parameters and will not display the indicator. 
  
 **CopyTo** can report global and individual errors, or errors that occur with one or more properties. These individual errors are placed in an **SPropProblemArray** structure. You can suppress error reporting at the property level by passing **null**, instead of a valid pointer, for the property problem array structure parameter. 
  
If you want to receive information about errors, pass a valid **SPropProblemArray** structure pointer in the  _lppProblems_ parameter. When **CopyTo** returns S_OK, check for possible errors with individual properties in the structure. When **CopyTo** returns an error, no information is returned in the **SPropProblemArray** structure. Instead, call [IMAPIProp::GetLastError](imapiprop-getlasterror.md) to retrieve detailed error information. 
  
If **CopyTo** returns S_OK, free the returned **SPropProblemArray** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
If you copy properties that are unique to the source object type, you must ensure that the destination object is of the same type. **CopyTo** does not prevent you from associating properties that typically belong to one type of object with another type of object. It is up to you to copy properties that make sense for the destination object. For example, you should not copy message properties to an address book container. 
  
To ensure that you copy between objects of the same type, check that the source and destination object are the same type, either by comparing object pointers or calling [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx). Set the interface identifier pointed to by  _lpInterface_ to the standard interface for the source object. Also, be sure that the object type or **PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md)) property is the same for the two objects. For example, if you copy from a message, set  _lpInterface_ to IID_IMessage and the **PR_OBJECT_TYPE** for both objects to MAPI_MESSAGE. 
  
If an invalid pointer is passed in the  _lpDestObj_ parameter, the results are unpredictable. 
  
Excluding properties on a **CopyTo** call can be useful. For example, some objects have properties that are specific to a single instance of the object, such as the date and time of message delivery. To avoid copying a message's delivery time when you copy the message to a different folder, specify **PR_MESSAGE_DELIVERY_TIME** ([PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md)) in the property tag exclude array. To exclude a message's recipient list, add the **PR_MESSAGE_RECIPIENTS** ([PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) property to the exclude array. To exclude a message's attachments, add the **PR_MESSAGE_ATTACHMENTS** ([PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) property to the array.
  
Similarly, prevent the copying or moving of a folder or address book container's hierarchy or contents table by including **PR_CONTAINER_HIERARCHY** ([PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md)) or **PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md)) in the property tag exclude array.
  
To exclude properties from the copy or move operation, include their property tags in the  _lpExcludeProps_ parameter. If you pass the results of the **PROP_TAG** macro to build a property tag from a specific identifier in the property tag array, all properties with that identifier will be excluded. For example, the following entry in the property tag array causes all properties with an identifier of 0x8002 to be excluded, regardless of type: 
  
 `PROP_TAG(PT_LONG, 0x8002)`
  
The **PR_NULL** ([PidTagNull](pidtagnull-canonical-property.md)) property tag cannot be included in the  _lpExcludeProps_ array. 
  
The usefulness of the **CopyTo** feature for excluding interfaces is perhaps not as obvious as the usefulness of excluding properties. You can exclude an interface when you copy to an object that has no knowledge of a group of properties. For example, if you copy properties from a folder to an attachment, the only properties that the attachment can work with are the generic properties available with any [IMAPIProp](imapipropiunknown.md) implementation. By excluding [IMAPIFolder](imapifolderimapicontainer.md) from the copy operation, the attachment will not receive any of the more specific folder properties. 
  
When you use the  _rgiidExclude_ parameter to exclude an interface, it also excludes all interfaces derived from that interface. For example, excluding [IMAPIContainer](imapicontainerimapiprop.md) causes folders or address book containers to be excluded, depending on the type of provider. Do not exclude **IMAPIProp** or [IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28v=VS.85%29.aspx) because so many interfaces derive from them. 
  
Ignore MAPI_E_COMPUTED errors returned in the **SPropProblemArray** structure in the  _lppProblems_ parameter. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|File.cpp  <br/> |LoadFromMSG  <br/> |MFCMAPI uses the **IMAPIProp::CopyTo** method to copy properties from a .msg file to an [IMAPIMessageSite](imapimessagesiteiunknown.md) object.  <br/> |
|FolderDlg.cpp  <br/> |CFolderDlg::HandlePaste  <br/> |MFCMAPI uses the **IMAPIProp::CopyTo** method to copy properties from a source message to a target message during a paste operation.  <br/> |
   
## See also



[IMAPIFolder::CopyMessages](imapifolder-copymessages.md)
  
[IMAPIProp::GetLastError](imapiprop-getlasterror.md)
  
[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)
  
[IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md)
  
[IMAPISupport::DoCopyTo](imapisupport-docopyto.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[PidTagContainerContents Canonical Property](pidtagcontainercontents-canonical-property.md)
  
[PidTagContainerHierarchy Canonical Property](pidtagcontainerhierarchy-canonical-property.md)
  
[PidTagMessageAttachments Canonical Property](pidtagmessageattachments-canonical-property.md)
  
[PidTagMessageDeliveryTime Canonical Property](pidtagmessagedeliverytime-canonical-property.md)
  
[PidTagMessageRecipients Canonical Property](pidtagmessagerecipients-canonical-property.md)
  
[PidTagObjectType Canonical Property](pidtagobjecttype-canonical-property.md)
  
[SPropProblemArray](spropproblemarray.md)
  
[SPropTagArray](sproptagarray.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

