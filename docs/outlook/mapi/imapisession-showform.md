---
title: "IMAPISessionShowForm"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISession.ShowForm
api_type:
- COM
ms.assetid: 233cf936-34db-42d4-b5e3-17a93acb2009
description: "Last modified: March 09, 2015"
---

# IMAPISession::ShowForm

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Displays a form.
  
```cpp
HRESULT ShowForm(
  ULONG_PTR ulUIParam,
  LPMDB lpMsgStore,
  LPMAPIFOLDER lpParentFolder,
  LPCIID lpInterface,
  ULONG ulMessageToken,
  LPMESSAGE lpMessageSent,
  ULONG ulFlags,
  ULONG ulMessageStatus,
  ULONG ulMessageFlags,
  ULONG ulAccess,
  LPSTR lpszMessageClass
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the form.
    
 _lpMsgStore_
  
> [in] A pointer to the message store that contains the folder pointed to by the  _lpParentFolder_ parameter. 
    
 _lpParentFolder_
  
> [in] A pointer to the folder in which the message associated with the  _ulMessageToken_ parameter was created. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the message that is displayed in the form. The  _lpInterface_ parameter must be NULL or IID_IMessage. Passing NULL results in the standard interface, [IMessage](imessageimapiprop.md), being used. 
    
 _ulMessageToken_
  
> [in] The token that is associated with the message to be displayed in the form. The  _ulMessageToken_ parameter must be set to the contents of the  _lpulMessageToken_ parameter from the previous call to [IMAPISession::PrepareForm](imapisession-prepareform.md).
    
 _lpMessageSent_
  
> [in] Reserved; must be NULL. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how and whether the message is saved. The following flags can be set:
    
MAPI_NEW_MESSAGE 
  
> The message has never been saved (that is, its [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method has never been called). 
    
MAPI_POST_MESSAGE 
  
> The message should be saved to its parent folder. The message is not processed for sending but is posted to the folder instead. If this flag is not set, the message is copied to the Outbox and is processed for sending. 
    
 _ulMessageStatus_
  
> [in] A bitmask of flags copied from the **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property of the message associated with the token in the  _ulMessageToken_ parameter. The flags provide information about the state of the message. 
    
 _ulMessageFlags_
  
> [in] A bitmask of flags copied from the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of the message associated with the token in the  _ulMessageToken_ parameter. These flags provide further information about the state of the message. 
    
 _ulAccess_
  
> [in] A flag that indicates the permission level for the message that is displayed in the form. This information is copied from the **PR_ACCESS** ([PidTagAccess](pidtagaccess-canonical-property.md)) property of the message associated with the token in the  _ulMessageToken_ parameter. 
    
 _lpszMessageClass_
  
> [in] A pointer to the message class of the message being displayed in the form, copied from the **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property of the message associated with the token in the  _ulMessageToken_ parameter. 
    
## Return value

S_OK 
  
> The form was successfully displayed.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

The **IMAPISession::ShowForm** method displays a message form that has been prepared by the **IMAPISession::PrepareForm** method. 
  
## Notes to callers

You should have only a single reference to the message passed in the **PrepareForm** method's  _lpMessage_ parameter. 
  
Be aware that form implementations can return error values other than the ones documented by MAPI. If you can use these error values to make a more accurate determination of the error condition, do so. Otherwise, handle these errors as you would handle MAPI_E_CALL_FAILED. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFormFunctions.cpp  <br/> |OpenMessageModal  <br/> |MFCMAPI uses the **IMAPISession::ShowForm** method, together with the **PrepareForm** method, to display a message in a modal form.  <br/> |
   
## See also



[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)
  
[IMAPISession::PrepareForm](imapisession-prepareform.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

