---
title: "HandsOffFromNormal State"
description: This article describes allowed transitions of the HandsOffFromNormal state.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 1afe6a2e-a5e6-4844-9f82-908894fc6759
 
 
---

# HandsOffFromNormal State

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The HandsOffFromNormal state is very similar to the [HandsOffAfterSave](handsoffaftersave-state.md) state. It is part of the process of saving the contents of a form to permanent storage. When in this state, the form object should refrain from making changes to the in-memory copies of values of the message's properties, because there may not be another opportunity to save those changes. The following table describes allowed transitions from the HandsOffFromNormal state. 
  
|****IPersistMessage** method**|**Action**|**New state**|
|:-----|:-----|:-----|
|[IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md)(_pMessage !=_ NULL)  <br/> |Replace the message object's message with  _pMessage_, which is the replacement for the message revoked by the previous call to [IPersistMessage::HandsOffMessage](ipersistmessage-handsoffmessage.md). The data in the new message is guaranteed to be the same as in the revoked message. The message should not be marked as clean, nor should [IMAPIViewAdviseSink::OnSaved](imapiviewadvisesink-onsaved.md) be called after this call. If the **SaveCompleted** call succeeds, enter the [Normal](normal-state.md) state. Otherwise, stay in the HandsOffFromNormal state. |Normal or HandsOffFromNormal  <br/> |
|**IPersistMessage::SaveCompleted**(_pMessage ==_ NULL)  <br/> |Set the last error to E_UNEXPECTED. |HandsOffFromNormal  <br/> |
|**HandsOffMessage**, [IPersistMessage::Save](ipersistmessage-save.md), [IPersistMessage::InitNew](ipersistmessage-initnew.md), or [IPersistMessage::Load](ipersistmessage-load.md) <br/> |Set the last error to E_UNEXPECTED. |HandsOffFromNormal  <br/> |
|[IPersistMessage::GetLastError](ipersistmessage-getlasterror.md) <br/> |Return the last error. |HandsOffFromNormal  <br/> |
|Other [IPersistMessage : IUnknown](ipersistmessageiunknown.md) methods or methods from other interfaces  <br/> |Set the last error to E_UNEXPECTED. |HandsOffFromNormal  <br/> |
   
## See also



[Form States](form-states.md)

