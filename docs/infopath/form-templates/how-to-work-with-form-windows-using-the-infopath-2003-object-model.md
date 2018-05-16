---
title: "Work with Form Windows Using the InfoPath 2003 Object Model"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
keywords:
- infopath 2003-compatible form templates, form windows,form windows [InfoPath 2007], InfoPath 2003-compatible form templates
 
localization_priority: Normal
ms.assetid: fbcf3a04-ee0f-40a6-8edd-583ae203e2e1

description: "When working programmatically with an InfoPath form, you can write code to access the form's windows, and then customize some of the items that they contain. The InfoPath 2003-compatible object model supports access to a form's windows through the use of the WindowObject interface in association with the WindowsCollection interface."
---

# Work with Form Windows Using the InfoPath 2003 Object Model

When working programmatically with an InfoPath form, you can write code to access the form's windows, and then customize some of the items that they contain. The InfoPath 2003-compatible object model supports access to a form's windows through the use of the [WindowObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.WindowObject.aspx) interface in association with the [WindowsCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.WindowsCollection.aspx) interface. 
  
There are two types of windows in InfoPath:
  
- The editing window, which is used when a user fills out a form.
    
- The designing window, which is used when a user designs a form template.
    
When writing code in a form template, it is the editing window that provides the most useful functionality, because you can use a **WindowObject** instance that references it to access a variety of properties and methods that can be used to customize the form editing experience. 
  
## Overview of the WindowsCollection Interface

The **WindowsCollection** interface provides the following properties, which form template developers can use to manage the **WindowObject** instances that it contains. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Count](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Windows.Count.aspx) property  <br/> |Returns a count of the number of **Window** objects contained in the collection.  <br/> |
|[Item](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Windows.Item.aspx) property  <br/> |Returns a reference to the specified **Window** object.  <br/> > [!NOTE]> Visual C# accesses collections using an indexer instead of calling the **Item** property. For example,  `thisApplication.Windows[0].Caption`.           |
   
## Overview of the Window Object

The **WindowObject** interface provides the following methods and properties, which form developers can use to interact with an InfoPath window. Support for these methods and properties differ depending on the type of window ( [XdWindowType](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XdWindowType.aspx) ) you are working with. Some methods and properties work only with the editor window type ( **XdWindowType.xdEditorWindow**). The remaining methods and properties work with both the editor window type and the designer window type ( **XdWindowType.xdDesignerWindow**). Additionally, like all InfoPath object model members, when called from a form template, support for methods and properties can vary depending on the security level and how the form is deployed.
  
|**Name**|**Description**|**Window Type Support**|
|:-----|:-----|:-----|
|[Activate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Activate.aspx) method  <br/> |Designates the window as the currently active window.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[Active](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Active.aspx) property  <br/> |Returns a **Boolean** value indicating whether the window is the currently active window.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[Caption](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Caption.aspx) property  <br/> |A read/write property that returns or sets the caption text for the window represented by the **Window** object.  <br/> |Only the **xdEditorWindow** type  <br/> |
|[Close](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Close.aspx) method  <br/> |Closes a window.  <br/> |Only the **xdEditorWindow** type  <br/> |
|[CommandBars](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.CommandBars.aspx) property  <br/> |Returns a reference to the Microsoft Office **CommandBars** object.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[Height](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Height.aspx) property  <br/> |A read/write property of type long integer that specifies the height of the window represented by the **Window** object, measured in points.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[Left](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Left.aspx) property  <br/> |A read/write property of type long integer that specifies the horizontal position of the window represented by the **Window** object, measured in points.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[MailEnvelope](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.MailEnvelope.aspx) property  <br/> |Returns a reference to the [MailEnvelopeObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.MailEnvelopeObject.aspx) object.  <br/> |Only the **xdEditorWindow** type  <br/> |
|[TaskPanes](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.TaskPanes.aspx) property  <br/> |Returns a reference to the [TaskPanesCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.TaskPanesCollection.aspx) collection.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[Top](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Top.aspx) property  <br/> |A read/write property of type long integer that specifies the vertical position of the window represented by the **Window** object, measured in points.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[WindowType](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.WindowType.aspx) property  <br/> |Returns a number indicating the type of the window, based on the [XdWindowType](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XdWindowType.aspx) enumeration.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[Width](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.Width.aspx) property  <br/> |A read/write property of type long integer that specifies the width of the window represented by the **Window** object, measured in points.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[WindowState](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.WindowState.aspx) property  <br/> |A read/write property of type [XdWindowState](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XdWindowState.aspx) that returns or sets the state of the window represented by the **Window** object.  <br/> |Both the **xdDesignWindow** and **xdEditorWindow** types  <br/> |
|[XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Window2.XDocument.aspx) property  <br/> |Returns a reference to the [_XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument.aspx) object associated with the window.  <br/> |Only the **xdEditorWindow** type  <br/> |
   
## Using the WindowsCollection and Window Interfaces

The **WindowsCollection** interface can be accessed through the [Windows](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._Application2.Windows.aspx) property of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Application.aspx) interface. When using the **WindowsCollection** interface to access a form's windows, you use an indexer (for Visual C#) or pass a long integer to the **Item** property (for Visual Basic) to return a reference to a **WindowObject** interface instance. For example, the following code sets a reference to the first **WindowObject** contained in the **WindowsCollection**.
  
```cs
WindowObject objWindow = thisApplication.Windows[0];
```

```VB.net
Dim objWindow As WindowObject = thisApplication.Windows(0)
```

However, you can access the currently open window directly by using the [ActiveWindow](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._Application2.ActiveWindow.aspx) property of the **Application** interface, without going through the ** WindowsCollection **, as the following code demonstrates.
  
```cs
WindowObject objWindow = thisApplication.ActiveWindow;
```

```VB.net
Dim objWindow As WindowObject = thisApplication.ActiveWindow
```

> [!NOTE]
> When debugging an InfoPath managed-code project, the **ActiveWindow** property will always return **null** because the debugging window is active. 
  
A **WindowObject** can also be accessed by using the [Window](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.Window.aspx) property of the [View](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.aspx) interface, which is associated with the form's underlying XML document. The **View** property of the **XDocument** interface is used to access the **View** object. For example, the following code sets a reference to the **WindowObject** that is associated with the view of a form's underlying XML document. 
  
```cs
WindowObject objWindow = thisXDocument.View.Window;
```

```VB.net
Dim objWindow As WindowObject = thisXDocument.View.Window
```

> [!NOTE]
> Some of the properties and methods of the **Window** object are only for the editing window type; if used with the designing window type, they will return an error. The properties and methods that are supported for each window type are listed in the table shown earlier in this topic. You can use the **WindowType** property in your code to determine which type of window you are working with. 
  

