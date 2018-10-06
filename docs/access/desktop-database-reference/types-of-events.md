---
title: Types of Events
TOCTitle: Types of Events
ms:assetid: 94660fc1-65c3-1d21-c451-f3898014e0b6
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249660(v=office.15)
ms:contentKeyID: 48546414
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Types of Events


**Applies to**: Access 2013 | Office 2013



There are two basic types of events. "Will Events," which are called before an operation starts, usually include "Will" in their names — for example, **WillChangeRecordset** or **WillConnect**. Events that are called after an event has been completed usually include "Complete" in their names — for example, **RecordChangeComplete** or **ConnectComplete**. Exceptions exist — such as **InfoMessage** — but these occur after the associated operation has completed.

## Will Events

Event handlers called before the operation starts offer you the opportunity to examine or modify the operation parameters, and then either cancel the operation or allow it to complete. These event-handler routines usually have names of the form **Will*Event***.

## Complete Events

Event handlers called after an operation completes can notify your application that an operation has concluded. Such an event handler is also notified when a Will event handler cancels a pending operation. These event-handler routines usually have names of the form ***Event*Complete**.

Will and Complete events are typically used in pairs.

## Other Events

The other event handlers — that is, events whose names are not of the form **Will*Event*** or ***Event*Complete —** are called only after an operation completes. These events are **Disconnect**, **EndOfRecordset**, and **InfoMessage**.

