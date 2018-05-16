---
title: "MAPI Notification Events"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: ef082d7b-9b2d-4267-beb5-d3ed1d9c7bbf
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Notification Events

  
  
**Applies to**: Outlook 
  
When client applications register for event notification, they must specify one or more events. The events that they can specify depend on the set of events that the intended advise source supports. There are ten types of notifications that clients and service providers can register for, each represented by a constant. Status object notification is an exception. Status object notification is an internal MAPI notification; clients cannot register for it and service providers cannot generate it. The following table describes the types of events and the advise source objects that can support them. The event constant is included with the event type.
  
|**Event type**|**Description**|**Advise source objects**|
|:-----|:-----|:-----|
|Critical error ( _fnevCriticalError_)  <br/> |A global error or event has occurred, such as a session shutdown in progress.  <br/> |Session, all types of message store and address book objects, table, status  <br/> |
|Object modified ( _fnevObjectModified_)  <br/> |A MAPI object has changed.  <br/> |Folders, messages, all types of address book objects  <br/> |
|Object created ( _fnevObjectCreated_)  <br/> |A MAPI object has been created.  <br/> |Folders, messages, all types of address book objects  <br/> |
|Object moved ( _fnevObjectMoved_)  <br/> |A MAPI object has been moved.  <br/> |Folders, messages, all types of address book objects  <br/> |
|Object deleted ( _fnevObjectDeleted_)  <br/> |A MAPI object has been deleted.  <br/> |Folders, messages, all types of address book objects  <br/> |
|Object copied ( _fnevObjectCopied_)  <br/> |A MAPI object has been copied.  <br/> |Folders, messages, all types of address book objects  <br/> |
|Extended event ( _fnevExtended_)  <br/> |An internal event defined by a particular service provider has occurred.  <br/> |Any advise source object  <br/> |
|Search complete ( _fnevSearchComplete_)  <br/> |A search operation has finished and the results of the search are available.  <br/> |Folders  <br/> |
|Table modified ( _fnevTableModified_)  <br/> |Information in a MAPI table object has changed.  <br/> |Tables  <br/> |
|New mail ( _fnevNewMail_)  <br/> |A message has been delivered and is waiting to be processed.  <br/> |Message store, folders  <br/> |
   
The extended event is defined by a service provider to represent an event that cannot be covered by any of the other predefined events. Only clients that know before they register that a service provider supports an extended event can register for that event. It is not possible for clients to determine without advance knowledge if a service provider supports an extended event and, if it does, how to handle such an event when it is received.
  

