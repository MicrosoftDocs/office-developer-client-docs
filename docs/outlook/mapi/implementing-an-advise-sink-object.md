---
title: "Implementing an Advise Sink Object"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 7461c4f6-7030-4ba2-ada4-26ebfbbfa001
description: "Last modified: March 09, 2015"
---

# Implementing an Advise Sink Object

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
A client can either implement its own advise sink objects or use a utility function, [HrAllocAdviseSink](hrallocadvisesink.md). **HrAllocAdviseSink** creates an advise sink object with an implementation of **OnNotify** that invokes a callback function. 
  
There are advantages and disadvantages to using **HrAllocAdviseSink**. It can save work, but it provides no control over reference counting the advise sink object that it creates. Therefore, clients that need to carefully control their advise sink's release or that have interdependencies between their advise sink and another client object should construct their own **IMAPIAdviseSink** implementation and avoid using **HrAllocAdviseSink** altogether. 
  
A client implementing its own advise sink should make it an independent object not related to or dependent upon any other objects so as to eliminate potential complications in reference counting and object release. However, if you must implement your advise sink as part of another object or include a back pointer to another object as a data member, it is recommended that two separate reference counts be maintained: one for the object referenced by the advise sink and one for the advise sink. 
  
When the reference count of the referenced object falls to zero, all of its methods can fail and its vtable can be destroyed, but the memory for the advise sink must remain intact until after its reference count also falls to zero. This means that the advise sink's **Release** method must decrement its reference count and finish destroying the object when that count reaches zero. If two separate reference counts are not maintained, it would be easy to inadvertently destroy the advise sink as part of the encompassing object's **Release** process. 
  
Clients using **HrAllocAdviseSink** to implement an advise sink must be equally careful not to include their callback function as a method in another advise sink object. For C++ clients, it is tempting to do this and pass the  _this_ pointer as a parameter. This is a dangerous strategy because clients typically free an object when its reference count reaches zero. Freeing the memory for the advise sink object would render the  _this_ pointer invalid. 
  
Depending on the type of event and the advise source, your **OnNotify** method can handle events in various ways. The following table offers suggestions in how to handle some of the standard events. 
  
|**Type of event**|**Handling in OnNotify**|
|:-----|:-----|
|Object moved  <br/> |If the moved object's original parent is related to the new parent, update the view beginning with the folder or address book container highest in the hierarchy. If the two parent containers are unrelated, update both of their views.  <br/> |
|New message  <br/> |Change the user interface to inform the user of the arrival of one or more new messages. Place the receive folder in the current view.  <br/> |
|Error  <br/> |For all objects except the session, log the error if necessary and return. For the session object, log off if possible.  <br/> |
|Search complete  <br/> |No processing necessary.  <br/> |
   
> [!NOTE]
> Notification handlers should be reentrant. 
  

