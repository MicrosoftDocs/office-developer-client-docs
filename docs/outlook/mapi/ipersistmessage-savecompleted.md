---
title: "IPersistMessageSaveCompleted"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPersistMessage.SaveCompleted
api_type:
- COM
ms.assetid: 83161011-90b4-49cb-9bcd-153a21a10977
description: "Last modified: March 09, 2015"
---

# IPersistMessage::SaveCompleted

  
  
**Applies to**: Outlook 
  
Notifies the form that a save operation has been completed. 
  
```
HRESULT SaveCompleted(
  LPMESSAGE pMessage
);
```

## Parameters

 _pMessage_
  
> [in] A pointer to the newly saved message.
    
## Return value

S_OK 
  
> The notification was successful.
    
E_INVALIDARG 
  
> The  _pMessage_ parameter is NULL and the form is either in the [HandsOffFromNormal](handsofffromnormal-state.md) or [HandsOffAfterSave](handsoffaftersave-state.md) state. 
    
E_UNEXPECTED 
  
> The form is not in one of the following states:
    
    - HandsOffFromNormal
    
    - HandsOffAfterSave
    
    - [NoScribble](noscribble-state.md)
    
## Remarks

The **IPersistMessage::SaveCompleted** method is called by a form viewer to notify the form that all pending changes have been saved. **SaveCompleted** should be called only when the form is in one of the following states: 
  
- HandsOffFromNormal
    
- HandsOffAfterSave
    
- NoScribble
    
## Notes to Implementers

There are several possible actions that the **SaveCompleted** method can perform, depending on what the message pointer parameter contains, and what state the message is in. However, when an action is successful, always save the current state of the message that the  _pMessage_ parameter points to and transition the form to its [Normal](normal-state.md) state. 
  
The following table describes the conditions that affect the actions you should take in your implementation of **SaveCompleted**.
  
|**Condition**|**Action**|
|:-----|:-----|
|The  _pMessage_ parameter is NULL and the  _fSameAsLoad_ parameter of the [IPersistMessage::Save](ipersistmessage-save.md) method is set to TRUE.  <br/> |Call the [IMAPIViewAdviseSink::OnSaved](imapiviewadvisesink-onsaved.md) method of all registered viewers, mark the form as clean, and return S_OK.  <br/> |
|The  _pMessage_ parameter is NULL and the  _fSameAsLoad_ parameter of the **IPersistMessage::Save** method is set to FALSE.  <br/> |Return S_OK.  <br/> |
|The form is in the HandsOffFromNormal state.  <br/> |Release the current message and replace it with the message pointed to by the  _pMessage_ parameter. Call the replacement message's [IUnknown::AddRef](http://msdn.microsoft.com/library/b4316efd-73d4-4995-b898-8025a316ba63%28Office.15%29.aspx) method and return S_OK.  <br/> |
|The form is in the HandsOffAfterSave state.  <br/> |Call the **IMAPIViewAdviseSink::OnSaved** method of all registered viewers, mark the form as clean, and return S_OK.  <br/> |
|The form is in the [NoScribble](noscribble-state.md) state.  <br/> |Release the current message and replace it with the message pointed to by  _pMessage_. Call the replacement message's **IUnknown::AddRef** method. Call the **IMAPIViewAdviseSink::OnSaved** method of all registered viewers, mark the form as clean, and return S_OK.  <br/> |
|The form is in one of the HandsOff states and the  _pMessage_ parameter is set to NULL.  <br/> |Return E_INVALIDARG.  <br/> |
|The form is in a state other than one of the HandsOff states or the NoScribble state.  <br/> |Return E_UNEXPECTED.  <br/> |
   
For more information about saving storage objects, see the documentation for the [IPersistStorage::SaveCompleted](http://msdn.microsoft.com/library/_com_ipersiststorage_savecompleted%28Office.15%29.aspx) or [IPersistFile::SaveCompleted](http://msdn.microsoft.com/library/_com_ipersistfile_savecompleted%28Office.15%29.aspx) methods. 
  
## See also

#### Reference

[IPersistMessage : IUnknown](ipersistmessageiunknown.md)
#### Concepts

[Form States](form-states.md)
#### Other resources

[IPersistStorage::SaveCompleted](http://msdn.microsoft.com/library/_com_ipersiststorage_savecompleted%28Office.15%29.aspx)
  
[IPersistFile::SaveCompleted](http://msdn.microsoft.com/library/_com_ipersistfile_savecompleted%28Office.15%29.aspx)

