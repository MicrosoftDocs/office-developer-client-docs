---
title: "Work with Form Windows"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
keywords:
- windowscollection [infopath 2007],form windows [InfoPath 2007],Window class [InfoPath 2007]
 
localization_priority: Normal
ms.assetid: 32ae2427-882b-45f8-8754-0e8c27fc23ba
description: "When working programmatically with an InfoPath form, you can write code to access the form's windows, and then customize some of the items that they contain. The InfoPath object model provided by the Microsoft.Office.InfoPath namespace supports access to a form's windows through the use of the Window class in association with the WindowCollection class."
---

# Work with Form Windows

When working programmatically with an InfoPath form, you can write code to access the form's windows, and then customize some of the items that they contain. The InfoPath object model provided by the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace supports access to a form's windows through the use of the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) class in association with the [WindowCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.aspx) class. 
  
> [!NOTE]
> The classes for working with a form's windows are available only when working with an **InfoPath Editor Form**. If a form template's **Compatibility** setting is **Web Browser Form**, these classes are not available. 
  
There are two types of windows in InfoPath: 
  
- The editing window that is used when a user fills out a form.
    
- The designing window that is used when a user designs a form template.
    
When writing code in a form template, it is the editing window that provides the most useful functionality, because you can use a [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) object that represents the current window to access a variety of properties and methods that can be used to customize the form editing experience. 
  
## Overview of the WindowsCollection Class

The [WindowCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.aspx) class provides the following properties, which form template developers can use to manage the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) objects that it contains. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Count](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.Count.aspx) property  <br/> |Gets a count of the number of [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) objects contained in the collection.  <br/> |
|[Item](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.Item.aspx) property  <br/> |Gets a reference to the specified [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) object.  <br/> |
   
## Overview of the Window Class

The [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) class provides the following methods and properties, which form developers can use to interact with an InfoPath window. Support for these methods and properties differ depending on the type of window ( [WindowType](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowType.aspx) ) you are working with. Some methods and properties work only with the editor window type ( **WindowType.Editor**). The remaining methods and properties work with both the editor window type and the designer window type ( **WindowType.Designer**). Additionally, like all InfoPath object model members, when called from a form template, support for methods and properties can vary depending on the security level and how the form is deployed.
  
|**Name**|**Description**|**Window Type Support**|
|:-----|:-----|:-----|
|[Activate](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Activate.aspx) method  <br/> |Activates (gives focus to) the window.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[Active](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Active.aspx) property  <br/> |Gets a **Boolean** value indicating whether the window is the currently active window.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[Caption](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Caption.aspx) property  <br/> |Gets or sets the caption text for the window represented by the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) object.  <br/> |Only **Editor** type  <br/> |
|[Close()](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Close.aspx) method  <br/> |Closes the window prompting to save changes to any unsaved form, or form with changes that have not been saved.  <br/> |Only **Editor** type  <br/> |
|[Close(Boolean)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Close.aspx) method  <br/> |Closes the window and optionally forces an unsaved form or form with unsaved changes to be closed without saving.  <br/> |Only **Editor** type  <br/> |
|[CommandBars](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.CommandBars.aspx) property  <br/> |Gets a reference to the Microsoft Office **CommandBars** collection that is associated with the window.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[Height](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Height.aspx) property  <br/> |Gets or sets the height of the window, measured in points.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[Left](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Left.aspx) property  <br/> |Gets or sets the horizontal position of the window, measured in points.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[MailEnvelope](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.MailEnvelope.aspx) property  <br/> |Gets a reference to the [MailEnvelope](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.MailEnvelope.aspx) class.  <br/> |Only **Editor** type  <br/> |
|[TaskPanes](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.TaskPanes.aspx) property  <br/> |Gets a reference to the [TaskPaneCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.TaskPaneCollection.aspx) collection.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[Top](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Top.aspx) property  <br/> |Gets or sets the vertical position of the window, measured in points.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[Width](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.Width.aspx) property  <br/> |Gets or set the width of the window, measured in points.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[WindowState](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.WindowState.aspx) property  <br/> |Gets or sets the state of the window as a [WindowState](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowState.aspx) value.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[WindowType](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.WindowType.aspx) property  <br/> |Gets the type of the window as an [WindowType](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowType.aspx) enumeration value.  <br/> |Both **Designer** and **Editor** type  <br/> |
|[XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.XmlForm.aspx) property  <br/> |Returns a reference to the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) object associated with the window.  <br/> |Only **Editor** type  <br/> |
   
## Using the WindowsCollection and Window Classes

The [WindowCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.aspx) class can be accessed through the [Windows](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.Windows.aspx) property of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.aspx) class. When using the [WindowCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.aspx) class to access a form's windows, you use an indexer (for Visual C#) or pass a long integer to the **Item** property (for Visual Basic) to return a reference to a [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) object instance. For example, the following code sets a reference to the first [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) object contained in the [WindowCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.aspx) for the current InfoPath session. 
  
```cs
Window myWindow = this.Application.Windows[0];
```

```VB.net
Dim myWindow As Window = Me.Application.Windows(0)
```

You can access the currently open window directly using the [ActiveWindow](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.ActiveWindow.aspx) property of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.aspx) class, without going through the [WindowCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WindowCollection.aspx) , as shown in the following line of code. 
  
```cs
Window myWindow = this.Application.ActiveWindow;
```

```VB.net
Dim myWindow As Window = Me.Application.ActiveWindow
```

A [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) object can also be accessed by using the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.View.Window.aspx) property of the [View](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.View.aspx) class, which represents the current view that is being used to work with the form's underlying XML document. The [CurrentView](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.CurrentView.aspx) property of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class is used to access a [View](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.View.aspx) object that represents the current view. For example, the following code sets a reference to the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) that is associated with the current view. 
  
```cs
Window myWindow = this.CurrentView.Window;
```

```VB.net
Dim myWindow As Window = Me.CurrentView.Window
```

> [!NOTE]
> Some of the properties and methods of the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) class are only for the editing window type; if used with the designing window type, they will return an error. Which properties and methods are supported for each window type are listed in the table earlier in this topic. You can use the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) property in your code to determine which type of window you are working with. 
  

