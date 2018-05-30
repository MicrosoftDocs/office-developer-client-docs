---
title: "NoScribble State"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 0246138f-c55e-4353-8e53-e973f524d52c
description: "Last modified: March 09, 2015"
 
 
---

# NoScribble State

  
  
**Applies to**: Outlook 
  
The NoScribble state indicates that changes to a message are being saved. The actual saving of values stored in the form object's user interface occurs when the form object's [IPersistMessage::Save](ipersistmessage-save.md) method is called by the client application. The following table describes allowed transitions from the NoScribble state. 
  
|****IPersistMessage** method**|**Action**|**New state**|
|:-----|:-----|:-----|
|[IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md)(_pMessage ==_ NULL)  <br/> |If  _fSameAsLoad_ flag was TRUE on the [IPersistMessage::Save](ipersistmessage-save.md) call that caused the form to enter the NoScribble state and the message has been modified, internally mark the changes as saved and call the [IMAPIViewAdviseSink::OnSaved](imapiviewadvisesink-onsaved.md) method.  <br/> |[Normal](normal-state.md) <br/> |
|**IPersistMessage::SaveCompleted**(_pMessage !=_ NULL)  <br/> |Call the [IPersistMessage::HandsOffMessage](ipersistmessage-handsoffmessage.md) method (similar to the OLE [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/1e5ef26f-d8e7-4fa6-bfc4-19dace35314d%28Office.15%29.aspx) method) followed by the normal **SaveCompleted** actions. If **SaveCompleted** was successful, enter the Normal state. Otherwise, enter the [HandsOffAfterSave](handsoffaftersave-state.md) state.  <br/> |Normal or HandsOffAfterSave  <br/> |
|**HandsOffMessage** <br/> |Recursively invoke the **HandsOffMessage** method on embedded messages or the OLE **IPersistStorage::HandsOffStorage** method on embedded OLE objects. Release the message object and any embedded messages or objects.  <br/> |HandsOffAfterSave  <br/> |
|**Save**, [IPersistMessage::InitNew](ipersistmessage-initnew.md), or [IPersistMessage::Load](ipersistmessage-load.md) <br/> |Set the last error to and return E_UNEXPECTED.  <br/> |NoScribble  <br/> |
|[IPersistMessage::GetLastError](ipersistmessage-getlasterror.md) <br/> |Return the last error.  <br/> |NoScribble  <br/> |
|Other [IPersistMessage : IUnknown](ipersistmessageiunknown.md) methods or methods from other interfaces  <br/> |Set the last error to and return E_UNEXPECTED.  <br/> |NoScribble  <br/> |
   
## See also



[Form States](form-states.md)

