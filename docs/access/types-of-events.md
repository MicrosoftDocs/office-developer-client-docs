---
title: "Types of Events"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 94660fc1-65c3-1d21-c451-f3898014e0b6
description: "There are two basic types of events.Will Events,which are called before an operation starts, usually includeWillin their names — for example, WillChangeRecordset or WillConnect . Events that are called after an event has been completed usually includeCompletein their names — for example, RecordChangeComplete or ConnectComplete . Exceptions exist — such as InfoMessage — but these occur after the associated operation has completed."
---

# Types of Events

There are two basic types of events. "Will Events," which are called before an operation starts, usually include "Will" in their names — for example, **WillChangeRecordset** or **WillConnect**. Events that are called after an event has been completed usually include "Complete" in their names — for example, **RecordChangeComplete** or **ConnectComplete**. Exceptions exist — such as **InfoMessage** — but these occur after the associated operation has completed. 
  
## Will Events

Event handlers called before the operation starts offer you the opportunity to examine or modify the operation parameters, and then either cancel the operation or allow it to complete. These event-handler routines usually have names of the form **Will *Event* **. 
  
## Complete Events

Event handlers called after an operation completes can notify your application that an operation has concluded. Such an event handler is also notified when a Will event handler cancels a pending operation. These event-handler routines usually have names of the form ** *Event*  Complete **. 
  
Will and Complete events are typically used in pairs.
  
## Other Events

The other event handlers — that is, events whose names are not of the form **Will *Event* ** or ** *Event*  Complete — ** are called only after an operation completes. These events are **Disconnect**, **EndOfRecordset**, and **InfoMessage**. 
  

