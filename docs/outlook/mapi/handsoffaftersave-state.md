---
title: "HandsOffAfterSave State"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: ffdfed49-2c52-445c-8051-6e566f61eedc
description: "Last modified: March 09, 2015"
 
 
---

# HandsOffAfterSave State

  
  
**Applies to**: Outlook 
  
The HandsOffAfterSave state is part of the process of saving the contents of a form to permanent storage. When in this state, the form object should refrain from making changes to the in-memory copies of values of the message's properties, because there may not be another opportunity to save those changes. The following table describes allowed transitions from the HandsOffAfterSave state.
  
|**IPersistMessage method**|**Action**|**New state**|
|:-----|:-----|:-----|
|[IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md)(_pMessage !=_ NULL)  <br/> |Open any embedded objects. The data in the message stored in  _pMessage_ is guaranteed to be the same as the message in the previous [IPersistMessage::Save](ipersistmessage-save.md) call. If the **SaveCompleted** call succeeds, enter the Normal state. Otherwise, set the last error to E_OUTOFMEMORY and stay in the HandsOffAfterSave state.  <br/> |[Normal](normal-state.md) or HandsOffAfterSave  <br/> |
|**IPersistMessage::SaveCompleted**(_pMessage ==_ NULL)  <br/> |Set the last error to E_INVALIDARG or E_UNEXPECTED.  <br/> |HandsOffAfterSave  <br/> |
|[IPersistMessage::HandsOffMessage](ipersistmessage-handsoffmessage.md), **Save**, or [IPersistMessage::InitNew](ipersistmessage-initnew.md) <br/> |Set the last error to and return E_UNEXPECTED.  <br/> |HandsOffAfterSave  <br/> |
|[IPersistMessage::Load](ipersistmessage-load.md) <br/> |Load the form object with data from the target message. This call can occur when the form object is going to the next or previous message in a folder.  <br/> |Normal  <br/> |
|[IPersistMessage::GetLastError](ipersistmessage-getlasterror.md) <br/> |Return the last error.  <br/> |HandsOffAfterSave  <br/> |
|Other [IPersistMessage : IUnknown](ipersistmessageiunknown.md) methods or methods from other interfaces  <br/> |Set the last error to and return E_UNEXPECTED.  <br/> |HandsOffAfterSave  <br/> |
   
## See also



[Form States](form-states.md)

