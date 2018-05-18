---
title: "IMAPIFormAdviseSinkOnActivateNext"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormAdviseSink.OnActivateNext
api_type:
- COM
ms.assetid: db621dfd-c6ad-42d2-8089-db40a63cab36
description: "Last modified: March 09, 2015"
---

# IMAPIFormAdviseSink::OnActivateNext

  
  
**Applies to**: Outlook 
  
Indicates whether the form can handle the message class of the next message to display.
  
```
HRESULT OnActivateNext(
  LPCSTR lpszMessageClass,
  ULONG ulMessageStatus,
  ULONG ulMessageFlags,
  LPPERSISTMESSAGE FAR * ppPersistMessage
);
```

## Parameters

 _lpszMessageClass_
  
> [in] A pointer to the message class of the next message.
    
 _ulMessageStatus_
  
> [in] A bitmask of client-defined or provider-defined flags, copied from the **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property of the next message to display, that provides status information regarding the contents table that the message is included in.
    
 _ulMessageFlags_
  
> [in] A pointer to a bitmask of flags copied from the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of the next message to display that indicates the current state of the message.
    
 _ppPersistMessage_
  
> [out] A pointer to a pointer to the [IPersistMessage](ipersistmessageiunknown.md) implementation for the form object used for the new form, if a new form is required. A pointer to NULL can be returned if the current form object can be used to display and save the next message. 
    
## Return value

S_OK 
  
> The notification was successful and the form can handle the next message.
    
S_FALSE 
  
> The form does not handle the message class of the next message.
    
## Remarks

Form viewers call the **IMAPIFormAdviseSink::OnActivateNext** method to help the form determine whether it can display the next message in a folder. The next message could be a message of any class, but typically it is of the same class or a related class. This makes the process of reading multiple messages of the same class more efficient by enabling client applications to reuse form objects whenever possible. 
  
Most form objects will use the message class pointed to by the  _lpszMessageClass_ parameter to determine whether they can handle the next message. Usually a form can handle messages that belong to classes of which the form's default class is a subclass, in addition to messages that belong to the default class. However, a form can use other factors to determine without question whether a message can be handled, such as the sent or unsent status of the next message. 
  
## Notes to Implementers

Return S_OK and NULL in the  _ppPersistMessage_ parameter if the form can handle the message class. If the form can create a new form that can handle the message that the form is unable to handle, follow these steps: 
  
1. Call your form's class factory to create an instance of a new form object.
    
2. Store that instance in the contents of the  _ppPersistMessage_ pointer parameter. 
    
3. Return S_OK.
    
The form viewer will load the message by using the [IPersistMessage::Load](ipersistmessage-load.md) method that belongs to the object pointed to by  _ppPersistMessage_.
  
If neither the form nor a form that you can create can handle the next message, return S_FALSE. However, in general, forms should not return this value because it causes decreased performance in the form viewer.
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFormFunctions.cpp  <br/> |CMyMAPIFormViewer::ActivateNext  <br/> |MFCMAPI uses the **IMAPIFormAdviseSink::OnActivateNext** method to implement the [IMAPIViewContext::ActivateNext](imapiviewcontext-activatenext.md) method.  <br/> |
   
## See also

#### Reference

[IMAPIViewContext::ActivateNext](imapiviewcontext-activatenext.md)
  
[IPersistMessage : IUnknown](ipersistmessageiunknown.md)
  
[IPersistMessage::Load](ipersistmessage-load.md)
  
[PidTagMessageFlags Canonical Property](pidtagmessageflags-canonical-property.md)
  
[PidTagMessageStatus Canonical Property](pidtagmessagestatus-canonical-property.md)
  
[IMAPIFormAdviseSink : IUnknown](imapiformadvisesinkiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

