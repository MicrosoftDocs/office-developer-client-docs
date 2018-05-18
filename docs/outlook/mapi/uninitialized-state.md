---
title: "Uninitialized State"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e071b50f-2e75-4537-ac7b-4a2f5ebea83d
description: "Last modified: March 09, 2015"
 
 
---

# Uninitialized State

  
  
**Applies to**: Outlook 
  
The Uninitialized state is the initial state form objects should be in when they are first created. Form objects become initialized with message data when a client application calls the [IPersistMessage::InitNew](ipersistmessage-initnew.md) or [IPersistMessage::Load](ipersistmessage-load.md) method on the form object. The following table describes allowed transitions from the Unitialized state. 
  
|**IPersistMessage method**|**Action**|**New state**|
|:-----|:-----|:-----|
|[IPersistMessage::InitNew](ipersistmessage-initnew.md) <br/> |Load the form object with default data.  <br/> |[Normal](normal-state.md) <br/> |
|[IPersistMessage::Load](ipersistmessage-load.md) <br/> |Load the form object with data from the target message.  <br/> |Normal  <br/> |
|[IPersistMessage::GetClassID](ipersistmessage-getclassid.md) <br/> |Return success, or set the last error to and return E_UNEXPECTED.  <br/> |Uninitialized  <br/> |
|[IPersistMessage::GetLastError](ipersistmessage-getlasterror.md) <br/> |Return the last error.  <br/> |Uninitialized  <br/> |
|Other [IPersistMessage : IUnknown](ipersistmessageiunknown.md) methods or methods from other interfaces  <br/> |Set the last error to and return E_UNEXPECTED.  <br/> |Uninitialized  <br/> |
   
## See also



[Normal State](normal-state.md)
  
[Form States](form-states.md)

