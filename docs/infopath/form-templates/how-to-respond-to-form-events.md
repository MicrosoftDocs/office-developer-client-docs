---
title: "Respond to Form Events"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
 
keywords:
- order of events [infopath 207],events [InfoPath 2007], responding,events [InfoPath 2007], order,InfoPath 2007, reponding to events,EventArgs classes [InfoPath 2007]
 
localization_priority: Normal
ms.assetid: 754db64b-179f-4385-8dd9-c20c9407b186
description: "You can write code to respond to various events that can occur as a user fills out a form. To work with events in InfoPath, you add event handlers while working with a form template in design mode."
---

# Respond to Form Events

You can write code to respond to various events that can occur as a user fills out a form. To work with events in InfoPath, you add event handlers while working with a form template in design mode.
  
InfoPath event handlers should always be created in design mode because InfoPath automatically adds the correct declaration for sinking the event to the **InternalStartup** method and inserts the event handler's code skeleton into a form's code file (FormCode.cs or FormCode.vb). After you have created an event handler, you should not alter its declaration in the form's code file. 
  
For information about creating the InfoPath event handlers, see [Add an Event Handler](how-to-add-an-event-handler.md).
  
## Overview of the Event Classes

The InfoPath model provided by the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace implements three classes that implement the 12 events that can be raised and handled by form template business logic. The following table lists each of the InfoPath event objects, the events they are associated with, and a description of the functionality they provide. 
  
|**Name**|**Events**|**Description**|
|:-----|:-----|:-----|
|[ButtonEvent](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.ButtonEvent.aspx) <br/> |[Clicked](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.ButtonEvent.Clicked.aspx) <br/> |The **ButtonEvent** class implements the **Clicked** event that is raised when a **Button** control is clicked on a form.  <br/> |
|[FormEvents](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.aspx) <br/> |[ContextChanged](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.ContextChanged.aspx) <br/> [Loading](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Loading.aspx) <br/> [Merge](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Merge.aspx) <br/> [Save](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Save.aspx) <br/> [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) <br/> [Submit](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Submit.aspx) <br/> [VersionUpgrade](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.VersionUpgrade.aspx) <br/> [ViewSwitched](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.ViewSwitched.aspx) <br/> |The **FormEvents** class implements the events that are specific to an InfoPath form template itself:  <br/> **ContextChanged** <br/> Occurs after the context node changes.  <br/> **Loading** <br/> Occurs when the form template has been loaded, but before any views have been initialized.  <br/> **Merge** <br/> Occurs when the **Merge Forms** command is invoked from the user interface, or InfoPath is started with the  `/aggregate` command-line switch.  <br/> **Save** <br/> Occurs when the **Save** or **Save As** commands are used from the user interface, or when the [Save](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Save.aspx) and [SaveAs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SaveAs.aspx) methods of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class are used.  <br/> **Sign** <br/> Occurs after a set of signed data has been selected to sign through the **Digital Signatures** dialog box.  <br/> **Submit** <br/> Occurs when the **Submit** command is used from the user interface, or the [Submit](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Submit.aspx) method of the **XmlForm** class is used.  <br/> **VersionUpgrade** <br/> Occurs when the version number of the form being opened is older than the version number of the form template on which it is based.  <br/> **ViewSwitched** <br/> Occurs after a view of a form has been successfully switched.  <br/> |
|[XmlEvent](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.aspx) <br/> |[Changed](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.Changed.aspx) <br/> [Changing](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.Changing.aspx) <br/> [Validating](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.Validating.aspx) <br/> |Implements the events raised by changes to the data in the underlying XML document of a form instance:  <br/> **Changed** <br/> Occurs after changes to a form's underlying XML document have been accepted and after the **Validating** event has occurred.  <br/> **Changing** <br/> Occurs after changes to a form's underlying XML document have been made but before the changes have been accepted.  <br/> **Validating** <br/> Occurs after changes to a form's underlying XML document have been accepted but before the **Changed** event has occurred.  <br/> The **XmlEvent** class also implements the [RaiseUndoRedoForChanged](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.RaiseUndoRedoForChanged.aspx) property, which gets or sets whether the **Changed** event will be raised when an undo or redo operation occurs.  <br/> |
   
> [!NOTE]
>  The **Changed** and **Changing** events fire only once when a change is made in a non-blank field in the form, whereas the comparable events in InfoPath 2003 and the InfoPath 2003-compatible object model provided by the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace ( [OnBeforeChange](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._DataDOMEventSink_Event.OnBeforeChange.aspx) and [OnAfterChange](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._DataDOMEventSink_Event.OnAfterChange.aspx) ) fire twice on changes to a non-blank field: once when the old value is deleted, and again when the new value is inserted. 
  
## Overview of the EventArgs Classes

Each of the 12 events have an **EventArgs** object associated with the event that are passed to the event handler for the event to provide state information and other functionality that can be used in the event handler code. The following table lists the InfoPath events with their associated **EventArgs** objects and a brief description of the functionality provided by the properties and methods of the object. For details on the specific properties and methods of the object, click the name of the **EventArgs** object in the table, and then click on the Members link in the topic. 
  
|**Event**|**EventsArgs Class**|**Description**|
|:-----|:-----|:-----|
|**Clicked** <br/> |[ClickedEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.ClickedEventArgs.aspx) <br/> |Gets the control ID.  <br/> Get an **XPathNavigator** object positioned at the innermost XML node of the form's underlying XML document that contains the **Button** control.  <br/> |
|**ContextChanged** <br/> |[ContextChangedEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.ContextChangedEventArgs.aspx) <br/> |Gets the type of context change that was performed when the event occurred.  <br/> Gets a value indicating whether the context change event occurred in response to undoing or redoing an operation.  <br/> Gets a reference to an **XPathNavigator** positioned at the context node that raised the event.  <br/> |
|**Loading** <br/> |[LoadingEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.LoadingEventArgs.aspx) <br/> |Specifies the view in which to open the form after loading.  <br/> Gets a reference to the **XmlFormCancelEventArgs** object.  <br/> Gets an **IDictionary** containing any input parameters specified using the  `/InputParameters` command-line option, or specified using query parameters in a URL to open the form.  <br/> |
|**Merge** <br/> |[MergeEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.MergeEventArgs.aspx) <br/> |Gets a reference to the **XmlFormCancelEventArgs** object.  <br/> Gets the count of the number of forms being merged in a merging operation.  <br/> Gets the zero-based index of the form that is currently being merged.  <br/> Gets or sets a value that is used with the **Cancel** property to determine whether to cancel only the current form or the entire merging operation.  <br/> Gets an **XPathNavigator** object positioned at the root node of the underlying XML document of the form that is currently being merged.  <br/> |
|**Save** <br/> |[SaveEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SaveEventArgs.aspx) <br/> |Performs the save operation requested by the user.  <br/> Gets a reference to the **SaveCancelEventArgs** object that can be used to cancel the event.  <br/> Gets the file name to be used in the event handler for the event.  <br/> Gets whether the save operation will be performed as a "save" operation or as a "save as" operation.  <br/> |
|**Sign** <br/> |[SignEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignEventArgs.aspx) <br/> |Gets or sets whether to display the **Digital Signatures** dialog box.  <br/> Gets the set of signable data that raised the event.  <br/> |
|**Submit** <br/> |[SubmitEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SubmitEventArgs.aspx) <br/> |Gets a reference to the **XmlFormCancelEventArgs** object for cancelling the event.  <br/> |
|**VersionUpgrade** <br/> |[VersionUpgradeEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.VersionUpgradeEventArgs.aspx) <br/> |Gets a reference to the **XmlFormCancelEventArgs** object for cancelling the event.  <br/> Gets the version number of the form document being upgraded.  <br/> Gets the version number of the form template associated with the form being upgraded.  <br/> |
|**ViewSwitched** <br/> |[ViewSwitchedEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.ViewSwitchedEventArgs.aspx) <br/> |The **ViewSwitchedEventArgs** class does not provide any properties and methods for the event other than those inherited from **System.Object**.  <br/> |
|**Changed** <br/> |[XmlEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEventArgs.aspx) <br/> |Gets an **XPathExpression** object which contains an XPath expression that returns the node that is currently being changed.  <br/> Gets the new value for the node being changed.  <br/> Gets an **XPathNavigator** object pointing to the node which is the parent of the node being deleted.  <br/> Gets the original value of the node that is being changed.  <br/> Gets an [XmlOperation](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlOperation.aspx) enumeration that indicates the type of operation that occurred when the node was changed.  <br/> Gets an **XPathNavigator** object pointing at the node that is being changed.  <br/> Gets a value that indicates whether the node being changed is part of an undo or redo operation.  <br/> |
|**Changing** <br/> |[XmlChangingEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlChangingEventArgs.aspx) <br/> |Gets an **XmlFormCancelEventArgs** object associated with the event.  <br/> Inherits all of the functionality listed above for the **XmlEventArgs** object.  <br/> |
|**Validating** <br/> |[XmlValidatingEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlValidatingEventArgs.aspx) <br/> |Creates a [FormError](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormError.aspx) object that contains custom error information with the specified values and adds it to the [FormErrorCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormErrorCollection.aspx) object of the form.  <br/> Inherits all of the functionality listed above for the **XmlEventArgs** object.  <br/> |
   
## Using the EventArgs Objects

When you create an event handler, InfoPath creates the event handler's declaration in the project's form code. In the declaration of the event handler, InfoPath uses **e** as the name of the parameter that is passed to the event handler. This parameter contains the **EventArgs** object that is associated with the event handler for providing state information and other functionality when the event occurs. 
  
For example, when you create an event handler for the **Loading** event in design mode (by clicking **Loading Event** menu on the **Developer** tab), InfoPath adds the declaration for the event handler that receives the [LoadingEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.LoadingEventArgs.aspx) object to the form code file, and then opens the code editor so that you can add your code to the following event handler declaration. 
  
```cs
public void FormEvents_Loading(object sender, LoadingEventArgs e)
{
   // Write your code here.
}
```

```vb
Public Sub FormEvents_Loading(ByVal sender As Object, _
   ByVal e As LoadingEventArgs)
   ' Write your code here.
End Sub
```

When writing code for an event handler, you can use the properties and methods implemented by the **EventArgs** object that is passed through the **e** parameter. For example, in the following **Changing** event handler, the [NewValue](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEventArgs.NewValue.aspx) property of the [XmlChangingEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlChangingEventArgs.aspx) object (which is inherited from the [XmlEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEventArgs.aspx) class) is used to check the value of the field that was just changed. If the user changed the field and left it blank, the [Message](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCancelEventArgs.Message.aspx) property of the [XmlFormCancelEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCancelEventArgs.aspx) class is accessed using the [CancelableArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlChangingEventArgs.CancelableArgs.aspx) property of the **XmlChangingEventArgs** object to display an error to the user, and the **XmlFormCancelEventArgs.Cancel** property is set to **true**, to cancel the event and roll back the changes the user made.
  
```cs
public void field1_Changing(object sender, LoadingEventArgs e)
{
   // Determine whether there is a new value.
   if (e.NewValue == "")
   {
      // The value is blank, so display an error message
      // and roll back the changes.
      e.CancelableArgs.Message = 
         "You must supply a value for this field.";
      e.CancelableArgs.Cancel = true;
      return;
   }
}
```

```vb
Public Sub field1_Changing(ByVal sender As Object, _
   ByVal e As LoadingEventArgs)
   ' Determine whether there is a new value.
   If (e.NewValue = "") Then
      ' The value is blank, so display an error message 
      ' and roll back the changes.
      e.CancelableArgs.Message = _
         "You must supply a value for this field."
      e.CancelableArgs.Cancel = True
      Return
   End If
End Sub
```


