---
title: "IMessageOpenAttach"
description: "Describes the syntax, parameters, return value, and remarks for IMessage OpenAttach, which opens an attachment."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMessage.OpenAttach
api_type:
- COM
ms.assetid: b680f5a7-0df3-4e7b-bf3b-f149eb42be8d
---

# IMessage::OpenAttach

**Applies to**: Outlook 2013 | Outlook 2016
 
Opens an attachment.
 
```cpp
HRESULT OpenAttach(
  ULONG ulAttachmentNum,
  LPCIID lpInterface,
  ULONG ulFlags,
  LPATTACH FAR * lppAttach
);
```

## Parameters

 _ulAttachmentNum_
 
> [in] Index number of the attachment to open, as stored in the attachment's **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property. This index number uniquely identifies the attachment in the message and is valid only in the context of the message.

 _lpInterface_
 
> [in] Pointer to the interface identifier (IID) representing the interface to be used to access the attachment. Passing NULL results in the attachment's standard interface, or **IAttach**, being returned.

 _ulFlags_
 
> [in] Bitmask of flags that controls how the attachment is opened. The following flags can be set:

MAPI_BEST_ACCESS
 
> Requests that the attachment be opened with the maximum network permissions allowed for the user and the maximum client application access. For example, if the client has read/write permission, the attachment should be opened with read/write permission; if the client has read-only access, the attachment should be opened with read-only access.

MAPI_DEFERRED_ERRORS
 
> Allows **OpenAttach** to return successfully, possibly before the attachment is fully available to the calling client. If the attachment is not available, making a subsequent call to it can cause an error.

MAPI_MODIFY
 
> Requests read/write permission. By default, attachments are opened with read-only access, and clients should not work on the assumption that read/write permission has been granted.

 _lppAttach_
  
> [out] Pointer to a pointer to the open attachment.

## Return value

S_OK
  
> The attachment was successfully opened.

## Remarks

The **IMessage::OpenAttach** method opens a message's attachment.
  
## Notes to callers

To open an attachment, you must have access to its attachment number or **PR_ATTACH_NUM** property. Call [IMessage::GetAttachmentTable](imessage-getattachmenttable.md) to retrieve the message's attachment table and locate the row that represents the attachment to be opened. See [Opening an Attachment](opening-an-attachment.md) for more information.
  
Do not try to open one attachment multiple times; the results are undefined and dependent on the message store provider.
  
You can request that the attachment be opened in read/write mode, instead of the default read-only mode. However, whether the attachment will actually be opened in read/write mode is up to the message store provider. You can either attempt to modify the attachment, preparing to handle possible failure, or check the level of access that was granted by retrieving the attachment's **PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)) property, if it is available.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|AttachmentsDlg.cpp Used to  <br/> |CAttachmentsDlg::OpenItemProp  <br/> |MFCMAPI uses the **IMessage::OpenAttach** method to open attachment objects,  <br/> |

## See also

[IMessage : IMAPIProp](imessageimapiprop.md)
[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
