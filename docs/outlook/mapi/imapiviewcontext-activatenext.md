---
title: "IMAPIViewContextActivateNext"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewContext.ActivateNext
api_type:
- COM
ms.assetid: 25ce90ac-526e-48a0-9edb-bd266375d4f4
description: "Last modified: March 09, 2015"
---

# IMAPIViewContext::ActivateNext

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Activates the next or previous message in the view order. 
  
```
HRESULT ActivateNext(
ULONG ulDir,
LPCRECT prcPosRect
);
```

## Parameters

 _ulDir_
  
> [in] Status flags giving information about the message to be activated. Valid flag settings are:
    
VCDIR_CATEGORY 
  
> The viewer should activate a message in another category of the view. The message to be activated is: 
    
    - The first message in the next view category if this flag is **OR**ed with VCDIR_NEXT. 
    
    - The last message in the previous view category if this flag is **OR**ed with VCDIR_PREV and the previous category is expanded. 
    
    - The first message in the previous view category if this flag is **OR**ed with VCDIR_PREV and the previous category is not expanded. In this case the previous category undergoes automatic expansion. 
    
VCDIR_DELETE 
  
> The viewer should activate the next or previous message because the current message has been deleted. 
    
VCDIR_MOVE 
  
> The viewer should activate the next or previous message because the current message has been moved. 
    
VCDIR_NEXT 
  
> The viewer should activate the next message in the view order. 
    
VCDIR_PREV 
  
> The viewer should activate the previous message in the view order. 
    
VCDIR_UNREAD 
  
> The viewer should activate the next or previous unread message in the view order. 
    
 _prcPosRect_
  
> [in] Pointer to a Windows **RECT** structure containing the size and position of the window to be used to display the activated message. 
    
## Return value

S_OK 
  
> The message was activated successfully. 
    
S_FALSE 
  
> The message was activated successfully, but a different type of form was opened in the process.
    
## Remarks

Form objects call the **IMAPIViewContext::ActivateNext** method to change what message is displayed to the user. The value passed in the  _ulDir_ parameter indicates which message should be activated and, in some cases, why. The VCDIR_NEXT and VCDIR_PREVIOUS flags correspond to users choosing the **Next** or **Previous** command in a view, respectively. These operations usually correspond to moving up or down one message in the form viewer's list of messages. 
  
The VCDIR_DELETE and VCDIR_MOVE flags are set by the [IMAPIMessageSite::DeleteMessage](imapimessagesite-deletemessage.md) and [IMAPIMessageSite::MoveMessage](imapimessagesite-movemessage.md) methods, respectively. Implementations of these methods call **ActivateNext** with the appropriate direction and then perform the requested operation on the message if the **ActivateNext** call did not fail. Form viewers typically enable users to specify the direction to move in the message list. 
  
## Notes to Implementers

Your implementation of [IMAPIViewContext::ActivateNext](imapiviewcontext-activatenext.md) makes the next or previous message in the folder, depending on the value of  _ulDir_, the current message. After **ActivateNext** returns, call [IMAPIMessageSite::GetMessage](imapimessagesite-getmessage.md) to get a pointer to the newly activated message. 
  
## Notes to Callers

If **ActivateNext** returns S_FALSE, or if a current message is not present, perform your normal shutdown procedure which should include calling your form's [IMAPIForm::ShutdownForm](imapiform-shutdownform.md) method. If a next or previous message is displayed, use the window rectangle passed in the  _prcPosRect_ parameter to display it. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::ActivateNext  <br/> |MFCMAPI implements the **IMAPIViewContext::ActivateNext** method in this function.  <br/> |
   
## See also

#### Reference

[IMAPIViewContext::GetViewStatus](imapiviewcontext-getviewstatus.md)
  
[IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

