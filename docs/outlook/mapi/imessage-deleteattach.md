---
title: "IMessageDeleteAttach"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMessage.DeleteAttach
api_type:
- COM
ms.assetid: 0a5cb49f-c4f3-4893-8616-80d6332efcfc
description: "Last modified: March 09, 2015"
---

# IMessage::DeleteAttach

  
  
**Applies to**: Outlook 
  
Deletes an attachment.
  
```
HRESULT DeleteAttach(
ULONG ulAttachmentNum,
ULONG_PTR ulUIParam,
LPMAPIPROGRESS lpProgress,
ULONG ulFlags
);
```

## Parameters

 _ulAttachmentNum_
  
> [in] Index number of the attachment to delete. This is the value for the attachment's **PR_ATTACH_NUM** ( [PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property.
    
 _ulUIParam_
  
> [in] Handle to the parent window of any dialog boxes or windows this method displays. The  _ulUIParam_ parameter is ignored unless the ATTACH_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _lpProgress_
  
> [in] Pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the ATTACH_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] Bitmask of flags that controls the display of a user interface. The following flag can be set:
    
ATTACH_DIALOG 
  
> Requests the display of a progress indicator as the operation proceeds.
    
## Return value

S_OK 
  
> The attachment was successfully deleted.
    
## Remarks

The **IMessage::DeleteAttach** method deletes an attachment from within a message. 
  
A deleted attachment is not permanently deleted until the message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method has been called. 
  
## Notes to Callers

Before calling **DeleteAttach**, call the **IUnknown::Release** method for the attachment and each of its streams. 
  
Because deleting an attachment can be a lengthy process, **DeleteAttach** provides the mechanism that displays a progress indicator. You can request the display of a progress indicator by passing a pointer to your [IMAPIProgress : IUnknown](imapiprogressiunknown.md) implementation or NULL if you do not have an implementation. You must also specify a window handle in the  _ulUIParam_ parameter and the ATTACH_DIALOG flag in the  _ulFlags_ parameter. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|AttachmentsDlg.cpp  <br/> |CAttachmentsDlg::OnDeleteSelectedItem  <br/> |MFCMAPI uses the **IMessage::DeleteAttach** method to delete the selected attachment.  <br/> |
   
## See also

#### Reference

[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

