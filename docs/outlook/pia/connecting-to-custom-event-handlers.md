---
title: Connecting to custom event handlers
TOCTitle: Connecting to custom event handlers
ms:assetid: 6e894c16-0fe9-4b86-b798-547b86f44cd8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb610520(v=office.15)
ms:contentKeyID: 55119783
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Connecting to custom event handlers

Outlook raises events to notify add-ins about something happening, such as the Inbox receiving a new mail item. Add-ins can specify to Outlook that upon the occurrence of a specific event, certain actions should take place. This alert and callback mechanism is supported by delegates of the .NET Framework. The Outlook Primary Interop Assembly (PIA) defines delegates to which you can connect callback methods to handle corresponding events. This topic describes this process of defining a callback method and connecting it as an event handler to the Outlook object.

## Creating a Callback method

A callback is a method that is implemented to handle the occurrence of a specific event and is executed by a notification source. In Outlook, add-ins can implement callback methods to respond to certain events raised by Outlook. This callback method must match the signature of the delegate of that event. For example, to implement an event handler for the [ItemSend](https://msdn.microsoft.com/en-us/library/bb647198\(v=office.15\)) event, you must declare the callback method that matches the signature of the corresponding delegate:

```csharp
public delegate void ApplicationEvents_11_ItemSendEventHandler(object Item, ref bool Cancel)
```


```vb
Public Delegate Sub ApplicationEvents_11_ItemSendEventHandler(_
    ByVal Item As Object, ByRef Cancel As Boolean)
```

When defining the callback method, ignore the Delegate keyword which otherwise would define another delegate. A sample callback method, MyItemSendEventHandler, is shown below:

```csharp
public void MyItemSendEventHandler(object Item, ref bool Cancel)
```


```vb
Public Sub MyItemSendEventHandler (_
    ByVal Item As Object, ByRef Cancel As Boolean)
…
End Sub
```

## Connecting a Callback method

After implementing a callback method for an event, you can connect it to the Outlook object so that Outlook knows to call the method as an event handler of that event. Note that an event can be handled by more than one event handler, and this is where delegates that assign event handling to event handlers come into play.

Continuing with the last example of specifying a event handler for the ItemSend event of the Application object, to connect MyItemSendEventHandler to the Application object in C\#, create an instance of the delegate object, pass MyItemSendEventHandler to the constructor of the delegate object, and then add this delegate object to the ItemSend event using the += operator:

```csharp
app.ItemSend += new ApplicationEvents_11_ItemSendEventHandler(MyItemSendEventHandler)
```

In Visual Basic, you use the AddHandler statement to associate the ItemSend event with the MyItemSendEventHandler event handler:

```vb
AddHandler app.ItemSend, AddressOf MyItemSendEventHandler
```

## See also

- [Events in the Outlook PIA](events-in-the-outlook-pia.md)
- [Objects in the Outlook PIA](objects-in-the-outlook-pia.md)

