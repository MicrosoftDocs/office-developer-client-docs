---
title: "IPersistMessageLoad"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IPersistMessage.Load
api_type:
- COM
ms.assetid: bd4646d2-8229-499d-91aa-3cbec72b9445
---

# IPersistMessage::Load

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Loads the form for a specified message.
  
```cpp
HRESULT Load(
  LPMESSAGESITE pMessageSite,
  LPMESSAGE pMessage,
  ULONG ulMessageStatus,
  ULONG ulMessageFlags
);
```

## Parameters

 _pMessageSite_
  
> [in] A pointer to the message site for the form to be loaded.
    
 _pMessage_
  
> [in] A pointer to the message for which the form should be loaded.
    
 _ulMessageStatus_
  
> [in] A bitmask of client-defined or provider-defined flags, copied from the message's **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property, that provide information about the state of the message.
    
 _ulMessageFlags_
  
> [in] A bitmask of flags, copied from the message's **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property, that provide further information about the state of the message.
    
## Return value

S_OK 
  
> The form was successfully loaded.
    
## Remarks

Form viewers call the **IPersistMessage::Load** method to load a form for an existing message. 
  
## Notes to implementers

 **Load** is called only when a form is in one of the following states: 
  
- [Uninitialized](uninitialized-state.md)
    
- [HandsOffAfterSave](handsoffaftersave-state.md)
    
- [HandsOffFromNormal](handsofffromnormal-state.md)
    
If a form viewer calls **Load** while the form is in any other state, the method returns E_UNEXPECTED. 
  
If your form has a reference to an active message site other than the one that is passed into **Load**, release the original site because it will no longer be used. Store the pointers to the message site and message from the  _pMessageSite_ and  _pMessage_ parameters and call both objects' [IUnknown::AddRef](https://msdn.microsoft.com/library/b4316efd-73d4-4995-b898-8025a316ba63%28Office.15%29.aspx) methods to increment their reference counts. 
  
After **AddRef** has completed, store the properties from the  _ulMessageStatus_ and  _ulMessageFlags_ parameters into the form. Transition the form to its [Normal](normal-state.md) state before displaying it, and notify registered viewers by calling their [IMAPIViewAdviseSink::OnNewMessage](imapiviewadvisesink-onnewmessage.md) methods. 
  
If no errors occur, return S_OK. 
  
## See also



[PidTagMessageFlags Canonical Property](pidtagmessageflags-canonical-property.md)
  
[PidTagMessageStatus Canonical Property](pidtagmessagestatus-canonical-property.md)
  
[IPersistMessage : IUnknown](ipersistmessageiunknown.md)


[Uninitialized State](uninitialized-state.md)
  
[HandsOffAfterSave State](handsoffaftersave-state.md)
  
[HandsOffFromNormal State](handsofffromnormal-state.md)
  
[Form States](form-states.md)


[IPersistStorage::Load](https://msdn.microsoft.com/library/34379b8d-4e00-49cd-9fd1-65f88746c61a.aspx)
  
[IPersistStream::Load](https://msdn.microsoft.com/library/351e1187-9959-4542-8778-925457c3b8e3.aspx)
  
[IPersistFile::Load](https://msdn.microsoft.com/library/8391aa5c-fe6e-4b03-9eef-7958f75910a5.aspx)

