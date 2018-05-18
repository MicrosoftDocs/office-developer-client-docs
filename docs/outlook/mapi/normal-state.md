---
title: "Normal State"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 8b2acad7-5ef8-44db-911f-3bd2a7ca2778
description: "Last modified: March 09, 2015"
 
 
---

# Normal State

  
  
**Applies to**: Outlook 
  
The Normal state is where the form object spends most of its time, waiting for client applications to initiate an action such as saving changes or closing the form. The following table describes allowed transitions from the Normal state.
  
|**IPersistMessage method**|**Action**|**New state**|
|:-----|:-----|:-----|
|[IPersistMessage::Save](ipersistmessage-save.md)(  _pMessage ==_ NULL,  _fSameAsLoad ==_ TRUE)  <br/> -or-  <br/> **IPersistMessage::Save**(  _pMessage !=_ NULL,  _fSameAsLoad ==_ FALSE)  <br/> |Recursively save any embedded OLE objects that have been modified. Save message data back to the message object. Store the  _fSameAsLoad_ flag for later use in the [NoScribble](noscribble-state.md) state.  <br/> |NoScribble  <br/> |
|**IPersistMessage::Save**(  _pMessage !=_ NULL,  _fSameAsLoad ==_ TRUE)  <br/> |This is the same as the previous case, except that this **Save** call is used in low-memory situations and must not fail for lack of memory.  <br/> |NoScribble  <br/> |
|[IPersistMessage::HandsOffMessage](ipersistmessage-handsoffmessage.md) <br/> |Recursively invoke the **HandsOffMessage** method on embedded messages or the OLE [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/1e5ef26f-d8e7-4fa6-bfc4-19dace35314d%28Office.15%29.aspx) method on embedded OLE objects. Release the message object and any embedded messages or objects.  <br/> |[HandsOffFromNormal](handsofffromnormal-state.md) <br/> |
|[IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md), [IPersistMessage::InitNew](ipersistmessage-initnew.md) or [IPersistMessage::Load](ipersistmessage-load.md) <br/> |Set the last error to and return E_UNEXPECTED.  <br/> |Normal  <br/> |
|[IPersistMessage::GetLastError](ipersistmessage-getlasterror.md) <br/> |Return the last error.  <br/> |Normal  <br/> |
|Other [IPersistMessage : IUnknown](ipersistmessageiunknown.md) methods or methods from other interfaces  <br/> |Implement as described in the documentation for the [IPersistMessage : IUnknown](ipersistmessageiunknown.md) interface.  <br/> |Normal  <br/> |
   
## See also



[Form States](form-states.md)

