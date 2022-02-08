---
title: "IMAPISessionPrepareForm"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.PrepareForm
api_type:
- COM
ms.assetid: 98c0eab1-fd7e-46c3-8619-ccd6dc7cf8f7
description: "Last modified: March 09, 2015"
---

# IMAPISession::PrepareForm

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a numeric token that the [IMAPISession::ShowForm](imapisession-showform.md) method uses to access a message. 
  
```cpp
HRESULT PrepareForm(
  LPCIID lpInterface,
  LPMESSAGE lpMessage,
  ULONG FAR * lpulMessageToken
);
```

## Parameters

 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the message. Passing **null** results in the standard interface, or [IMessage](imessageimapiprop.md), being used. The  _lpInterface_ parameter must be **null** or IID_IMessage. 
    
 _lpMessage_
  
> [in] A pointer to the message to be displayed in the form.
    
 _lpulMessageToken_
  
> [out] A pointer to a message token, which is used by the **IMAPISession::ShowForm** method to access the message pointed to by  _lpMessage_.
    
## Return value

S_OK 
  
> The form preparation was successful.
    
## Remarks

The **IMAPISession::PrepareForm** method creates a message token for the message pointed to by the  _lpMessage_ parameter and calls the message's [IUnknown::AddRef](https://msdn.microsoft.com/library/ms691379%28v=VS.85%29.aspx) method. This token is passed in the _ulMessageToken_ parameter to **IMAPISession::ShowForm**. 
  
## Notes to callers

If the call to **PrepareForm** succeeds, release the message pointed to by  _lpMessage_ by calling its [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) method before you call **ShowForm**. Failure to release the message before you call **ShowForm** can cause memory leaks. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFormFunctions.cpp  <br/> |OpenMessageModal  <br/> |MFCMAPI uses the **IMAPISession::PrepareForm** method, along with **IMAPISession::ShowForm**, to display a message in a modal form.  <br/> |
   
## See also



[IMAPISession::ShowForm](imapisession-showform.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

