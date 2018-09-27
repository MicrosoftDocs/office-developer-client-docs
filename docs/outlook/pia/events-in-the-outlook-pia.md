---
title: Events in the Outlook PIA
TOCTitle: Events in the Outlook PIA
ms:assetid: 1f9eafb3-6645-4e27-81fa-5d73bf94ae40
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb644571(v=office.15)
ms:contentKeyID: 55119782
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Events in the Outlook PIA

Browsing the Outlook Primary Interop Assembly (PIA), you might notice that many interfaces and event delegates are named after familiar names of objects and events in the Outlook object model. Unlike events in the COM type library, events in the Outlook PIA are not defined in the same interface as methods and properties of the same object. Event-related interfaces, delegates, and sink helper classes are either imported or created to support events in the Outlook PIA. This topic describes these event-related interfaces, delegates, and sink helper classes.

## Where Do the Event Interfaces, Delegates and Sink Helper Classes Come From

To create the Outlook PIA, Outlook uses the Type Library Importer (TLBIMP) in the .NET Framework to convert type definitions in the COM type library into equivalent definitions in a common language runtime (CLR) assembly. TLBIMP imports the following two types of interfaces for each object:

  - The primary interface (for example, the [\_Application](https://msdn.microsoft.com/en-us/library/bb611255\(v=office.15\)) interface)

  - The event interface (for example, the [ApplicationEvents\_11](https://msdn.microsoft.com/en-us/library/bb609229\(v=office.15\)) interface)

TLBIMP processes the imported interfaces and creates a number of interfaces, delegates, and classes, including the .NET interface (for example, the [Application](https://msdn.microsoft.com/en-us/library/bb646615\(v=office.15\)) interface). If the object has events, the following are created:

  - The .NET event interface (for example, the [ApplicationEvents\_11\_Event](https://msdn.microsoft.com/en-us/library/bb622725\(v=office.15\)) interface)

  - Delegate for each event (for example, the [ApplicationEvents\_11\_ItemSendEventHandler](https://msdn.microsoft.com/en-us/library/bb610818\(v=office.15\)) delegate)

  - Sink helper class (for example, [ApplicationEvents\_11\_SinkHelper](https://msdn.microsoft.com/en-us/library/bb609842\(v=office.15\)) class)

### Multiple Versions of Events

Some objects that have existed for multiple versions of Outlook have different implementations of events over the versions, and have had additional events added as new versions are released. To support events that vary over multiple versions, Outlook distinguishes these event-related interfaces, delegates, and classes by adding a version number to their names. For example:

  - The imported event interfaces of the Application object includes:
    
      - The earliest version for Outlook 98 and Outlook 2000: the [ApplicationEvents](https://msdn.microsoft.com/en-us/library/bb644093\(v=office.15\)) interface
    
      - The version for Outlook 2002: the [ApplicationEvents\_10](https://msdn.microsoft.com/en-us/library/bb647702\(v=office.15\)) interface
    
      - The version for Outlook 2003 and later releases: the [ApplicationEvents\_11](https://msdn.microsoft.com/en-us/library/bb609229\(v=office.15\)) interface

  - The .NET event interfaces created by TLBIMP for the Application object includes:
    
      - The earliest version for Outlook 98 and Outlook 2000: the [ApplicationEvents\_Event](https://msdn.microsoft.com/en-us/library/bb609380\(v=office.15\)) interface
    
      - The version for Outlook 2002: the [ApplicationEvents\_10\_Event](https://msdn.microsoft.com/en-us/library/bb610098\(v=office.15\)) interface
    
      - The version for Outlook 2003 and later releases: the [ApplicationEvents\_11\_Event](https://msdn.microsoft.com/en-us/library/bb622725\(v=office.15\)) interface

  - The delegates that TLBIMP creates for each event in each version of the Application object, for example, a delegate for each version of the ItemSend event:
    
      - The earliest version for Outlook 98 and Outlook 2000: the [ApplicationEvents\_ItemSendEventHandler](https://msdn.microsoft.com/en-us/library/bb622515\(v=office.15\)) delegate
    
      - The version for Outlook 2002: the [ApplicationEvents\_10\_ItemSendEventHandler](https://msdn.microsoft.com/en-us/library/bb646436\(v=office.15\)) delegate
    
      - The version for Outlook 2003 and later releases: the [ApplicationEvents\_11\_ItemSendEventHandler](https://msdn.microsoft.com/en-us/library/bb610818\(v=office.15\)) delegate

Logically, events that are added to a later version do not appear in event interfaces of earlier versions and do not have corresponding delegates in earlier versions. For example, the [AttachmentSelectionChange](https://msdn.microsoft.com/en-us/library/ff184926\(v=office.15\)) event was added to the [Explorer](https://msdn.microsoft.com/en-us/library/bb623678\(v=office.15\)) object in Outlook 2010, therefore, it is not part of these earlier event interfaces for the Explorer object:

  - ExplorerEvents interface

  - ExplorerEvents\_Event interface

On the other hand, you can find the event in the most recent .NET event interface, ExplorerEvents\_10\_Event, and its delegate for the Outlook 2010 version, [ExplorerEvents\_10\_AttachmentSelectionChangeEventHandler](https://msdn.microsoft.com/en-us/library/ff185177\(v=office.15\)).

## What the Event Interfaces, Delegates, and Sink Helper Classes Are For

Using the Application object as an example, this section describes what each interface and class listed above contains:

  - The primary interface, \_Application, defines all the methods and properties of Application. Except for a condition discussed below, typically you do not use this interface in code.

  - The events interfaces imported by TLBIMP, such as ApplicationEvents\_11 and ApplicationEvents\_10, define methods mapping to events of Application in the corresponding version of Outlook. You do not use this interface in code.

  - The events interfaces created by TLBIMP, such as ApplicationEvents\_11\_Event and ApplicationEvents\_10\_Event, define all the events of Application in the corresponding version of Outlook. When designing an event handler for an event in a specific version, you implement the event handler as a method and connect the method to the event defined in the corresponding version of the .NET events interface. Except for a condition discussed below, typically you do not reference the events interface in code.

  - The .NET interface, Application, inherits the \_Application interface and the ApplicationEvents\_11\_Event interface. Typically, this is the one interface you use in managed code to access the object, method, property, and the latest event members of the Application object. There are however two exceptions where you would not use the .NET interface but a different interface to connect to an event:
    
      - When you access an event that shares the same name as a method of that object, cast to the appropriate event interface to connect to the event. For example, to connect to the [Quit](https://msdn.microsoft.com/en-us/library/bb622595\(v=office.15\)) event, you cast to the ApplicationEvents\_11\_Event interface.
    
      - When you connect to an earlier version of an event that has been subsequently extended in a later version of Outlook, connect to the version of the event in the earlier interface. For example, if you want to connect to the version of the Quit event of the Application object implemented for Outlook 2002 instead of the latest version, connect to the [Quit](https://msdn.microsoft.com/en-us/library/bb609660\(v=office.15\)) event defined in the ApplicationEvents\_10\_Event interface, instead of the Quit event defined in the ApplicationEvents\_11\_Event interface.

  - Delegates provide a framework for you to create custom event handlers for specific events in a specific version of Outlook. For example, if you want to add a check for the existence of a subject line in an Outlook item just before you send it, you implement the check in a callback method that has the same signature as the delegate, ApplicationEvents\_11\_ItemSendEventHandler. Then you hook up the callback method as an event handler for the ItemSend event that is defined in the ApplicationEvents\_11\_Event interface. For more information about connecting the callback method as an event handler for an object, see [Connecting to Custom Event Handlers](connecting-to-custom-event-handlers.md).

  - The sink helper classes created by TLBIMP, for example, ApplicationEvents\_11\_SinkHelper and [ApplicationEvents\_10\_SinkHelper](https://msdn.microsoft.com/en-us/library/bb644070\(v=office.15\)), are event helper objects for Application events in the corresponding version of Outlook. Do not use these classes in code.

## See also

#### Concepts

[Relating the Outlook PIA with the Object Model](relating-the-outlook-pia-with-the-object-model.md)

[Objects in the Outlook PIA](objects-in-the-outlook-pia.md)

[Methods and Properties in the Outlook PIA](methods-and-properties-in-the-outlook-pia.md)



[Developing Managed Outlook Add-ins Using the Outlook PIA](developing-managed-outlook-add-ins-using-the-outlook-pia.md)

