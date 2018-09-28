---
title: Scoping variables appropriately in event handlers
TOCTitle: Scoping variables appropriately in event handlers
ms:assetid: 95b71535-abfd-43f1-a471-2026b522eac1
ms:contentKeyID: 55119788
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- vb
---

# Scoping variables appropriately in event handlers

A common mistake in programming event handlers is connecting the event handler to an object that has been declared with a scope too limited for the purpose of handling the event. The object must have a life that spans not just over the function that connects the callback method as an event handler of the object, but also over the callback method itself where the event is actually handled. Otherwise, if the object is out of scope and is no longer defined in the callback method, the callback method is not called and the event is not handled as desired.

The following example attempts to connect the MyNewInspector callback method to the [NewInspector](https://msdn.microsoft.com/en-us/library/bb612750\(v=office.15\)) event. However, the callback method is hooked up in the code sample to the NewInspector event of an [Inspectors](https://msdn.microsoft.com/en-us/library/bb623458\(v=office.15\)) object that has a scope limited to the Connect function. When the callback method is eventually called, the Connect function has already exited, the Inspectors object has already been garbage collected, and so MyNewInspector is never called.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;

class MyClass
{
    private Outlook.Application MyApp;

    public MyClass(Outlook.Application appOutlook)
    {
        MyApp = appOutlook;
    }

    // Connects the NewInspector event to my callback method
    public void Connect()
    {
        MyApp.Inspectors.NewInspector += new Outlook.
            InspectorsEvents_NewInspectorEventHandler(
            MyNewInspector);
    }

    public void MyNewInspector(Outlook.Inspector inspector)
    {
        MessageBox.Show("
            My event handler caught a NewInspector event");
    }
}
```

<br/>

The correct thing to do in this case is to store the Inspectors object in a more permanent variable whose lifetime spans over the entire MyClass, including the MyNewInspector callback method. In the following example, MyInspectors has a scope of the entire MyClass and ensures that the callback method is connected for the lifetime of the class.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;

class MyClass
{
    private Outlook.Application MyApp;
    private Outlook.Inspectors MyInspectors;

    public MyClass(Outlook.Application appOutlook)
    {
        MyApp = appOutlook;
    }

    // Connects the NewInspector event to my callback method
    public void Connect()
    {
        MyInspectors = MyApp.Inspectors;
        MyInspectors.NewInspector += new Outlook.
            InspectorsEvents_NewInspectorEventHandler(
            MyNewInspector);
    }

    public void MyNewInspector(Outlook.Inspector inspector)
    {
        MessageBox.Show("
            My event handler caught a NewInspector event");
    }
}
```

<br/>

By virtue of the syntactic differences in how various languages connect event handlers, this issue is less common in languages such as Visual Basic where you can connect an event specifying an instance of the parent object, and define the callback method at the same time. The following example in Visual Basic uses the Handles keyword to connect the Region\_Expanded callback method to the [Expanded](https://msdn.microsoft.com/en-us/library/bb609515\(v=office.15\)) event. An instance of the parent object, Region, has a scope that spans MyClass including the Region\_Expanded callback method.

```vb
Imports Outlook = Microsoft.Office.Interop.Outlook

Public Class MyClass
    ' The Region object has a lifetime spanning the class 
    ' including the callback method Region_Expanded
    Private WithEvents Region As Outlook.FormRegion
    ...
    Private Sub Region_Expanded() Handles Region.Expanded
        MsgBox("My EventHandler caught an Expanded event.")
    End Sub
End Class
```

In this example, because the Region\_Expanded callback method is connected to the Expanded event for the lifetime of the class, the callback method is called as appropriate.

## See also

- [Connecting to custom event handlers](connecting-to-custom-event-handlers.md)

