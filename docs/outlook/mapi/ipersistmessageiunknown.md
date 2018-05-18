---
title: "IPersistMessage  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPersistMessage
api_type:
- COM
ms.assetid: 40ec6dd4-2206-4e59-aafe-53aaf693f973
description: "Last modified: March 09, 2015"
---

# IPersistMessage : IUnknown

  
  
**Applies to**: Outlook 
  
Enables form viewers to handle the storage of a form and to transition between the various states.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Persist message objects  <br/> |
|Implemented by:  <br/> |Form objects  <br/> |
|Called by:  <br/> |Form viewers  <br/> |
|Interface identifier:  <br/> |IID_IPersistMessage  <br/> |
|Pointer type:  <br/> |LPPERSISTMESSAGE  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetLastError](ipersistmessage-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error in the form object.  <br/> |
|[GetClassID](ipersistmessage-getclassid.md) <br/> |Returns an identifier that represents the form server that can manage the form.  <br/> |
|[IsDirty](ipersistmessage-isdirty.md) <br/> |Checks the form for changes that were made since the last save.  <br/> |
|[InitNew](ipersistmessage-initnew.md) <br/> |Initializes a new message.  <br/> |
|[Load](ipersistmessage-load.md) <br/> |Loads the form for a specified message.  <br/> |
|[Save](ipersistmessage-save.md) <br/> |Saves a revised form back to the message from which it was loaded or created.  <br/> |
|[SaveCompleted](ipersistmessage-savecompleted.md) <br/> |Notifies the form that a save operation has been completed.  <br/> |
|[HandsOffMessage](ipersistmessage-handsoffmessage.md) <br/> |Causes the form to release its current message.  <br/> |
   
## Remarks

All forms are required to implement the **IPersistMessage** interface. 
  
 **IPersistMessage** works similarly to the OLE [IPersistStorage](http://msdn.microsoft.com/library/1c1a20fc-c101-4cbc-a7a6-30613aa387d7%28Office.15%29.aspx) interface. For more information, see the **IPersistStorage** methods. 
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

