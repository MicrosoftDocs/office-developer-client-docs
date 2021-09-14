---
title: Architecture of the Outlook PIA
TOCTitle: Architecture of the Outlook PIA
ms:assetid: 89577d14-e6e2-4270-8e72-b0adba378667
ms:mtpsurl: https://msdn.microsoft.com/library/office/bb646255(v=office.15)
ms:contentKeyID: 55119777
ms.date: 07/24/2014
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Architecture of the Outlook PIA

The Outlook Primary Interop Assembly (PIA) fully supports developing against the Outlook object model in managed code. However, when you look at the PIA in an object browser for the first time, you may be surprised by the many extra interfaces that the PIA contains, and the fact that not all method, property, and event members of an object are exposed by the same object interface. The topics in this section describe guidelines for how to access object members in code, and where to look for help for objects, methods, properties, and events.

## In this section

|Topic|Description|
|:----|:----------|
|[Relating the Outlook PIA with the object model](relating-the-outlook-pia-with-the-object-model.md) |Describes how objects and members in the COM-based Outlook object model are mapped to corresponding managed interfaces and classes in the PIA.|
|[Objects in the Outlook PIA](objects-in-the-outlook-pia.md) |Describes the typical .NET interfaces, classes, and delegates that are mapped to a COM object, and describes how to access an object in the PIA.|
|[Methods and properties in the Outlook PIA](methods-and-properties-in-the-outlook-pia.md) |Describes how to access methods and properties of an object in managed code by using the PIA.|
|[Events in the Outlook PIA](events-in-the-outlook-pia.md) |Describes event-related interfaces, delegates, and sink helper classes in the PIA.|

## See also

- [Setting up to use the Outlook PIA](setting-up-to-use-the-outlook-pia.md)
- [Developing managed Outlook add-ins using the Outlook PIA](developing-managed-outlook-add-ins-using-the-outlook-pia.md)
- [How do I... (Outlook 2013 PIA Reference)](how-do-i-outlook-2013-pia-reference.md)

