---
title: "Respond to Form Events Using the InfoPath 2003 Object Model"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
 
keywords:
- form templates [infopath 2007], responding to events,InfoPath 2003-compatible form templates, responding to form events
 
ms.localizationpriority: medium
ms.assetid: 59e9c1ed-32a8-4bcd-bdfc-9aa568a34d2a
description: "You can write code to respond to various events that can occur as a user fills out a form. To work with events in InfoPath, you create event handlers in the InfoPath designer."
---

# Respond to Form Events Using the InfoPath 2003 Object Model

You can write code to respond to various events that can occur as a user fills out a form. To work with events in InfoPath, you create event handlers in the InfoPath designer.
  
InfoPath event handlers should be created in the InfoPath designer because, when using the InfoPath 2003-compatible object model, InfoPath automatically adds the correct declaration and applies an attribute ([InfoPathEventHandlerAttribute](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.InfoPathEventHandlerAttribute.aspx) ) in a form's code file (FormCode.cs or FormCode.vb) to identify and sink the event handler. After you have created an event handler, you should not alter its declaration and attribute in the form's code file.
  
For information about creating the InfoPath event handlers, see [Add an Event Handler Using the InfoPath 2003 Object Model](how-to-add-an-event-handler-using-the-infopath-2003-object-model.md).
  
## Overview of the Event Objects

The InfoPath 2003-compatible object model implements nine event objects that are exposed in the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace. The following table lists each of the InfoPath event objects, the event handlers they are associated with, and a description of the functionality they provide.
  
|**Name**|**Event handlers**|**Description**|
|:-----|:-----|:-----|
|[DataDOMEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataDOMEvent.aspx) <br/> |[OnBeforeChange](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._DataDOMEventSink_Event.OnBeforeChange.aspx) <br/> [OnValidate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._DataDOMEventSink_Event.OnValidate.aspx) , [OnAfterChange](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._DataDOMEventSink_Event.OnAfterChange.aspx) <br/> |Returns a reference to a form's underlying XML document, the return status, and other properties that contain information about the XML node during an XML Document Object Model (DOM) change. Also includes a method for raising an error. |
|[DocActionEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DocActionEvent.aspx) <br/> |[OnClick](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._ButtonEventSink_Event.OnClick.aspx) <br/> |Returns a reference to a form's underlying XML document, the return status, and the source XML node during a button click in the form area. |
|[DocContextChangeEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DocContextChangeEvent.aspx) <br/> |[OnContextChange](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnContextChange.aspx) <br/> |Returns information about the XML Document Object Model (DOM) node that is the current context of the form's underlying XML document. |
|[DocEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DocEvent.aspx) <br/> |[OnSwitchView](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnSwitchView.aspx) , [OnAfterImport](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnAfterImport.aspx) <br/> |Returns a reference to a form's underlying XML document during a switch view or form merge operation. |
|[DocReturnEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DocReturnEvent.aspx) <br/> |[OnLoad](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnLoad.aspx) , [OnSubmitRequest](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnSubmitRequest.aspx) <br/> |Returns a reference to a form's underlying XML document and the return status during the loading or submission of a form. |
|[MergeEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.MergeEvent.aspx) <br/> |[OnMergeRequest](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnMergeRequest.aspx) <br/> |Returns properties and methods that can be used during an **OnMergeRequest** event to programmatically interact with a form's underlying XML document and to determine merge properties such as the number of files being merged. |
|[SaveEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.SaveEvent.aspx) <br/> |[OnSaveRequest](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnSaveRequest.aspx) <br/> |Returns a number of properties and methods that can be used during a save operation from the **OnSaveRequest** event handler to programmatically interact with a form's underlying XML document, determine save properties, and perform the save operation. |
|[SignEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.SignEvent.aspx) <br/> |[OnSign](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnSign.aspx) <br/> |Used to add additional data to the digital signature. |
|[VersionUpgradeEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.VersionUpgradeEvent.aspx) <br/> |[OnVersionUpgrade](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnVersionUpgrade.aspx) <br/> |Returns a reference to a form's underlying XML document, the return status, and the document and solution version numbers during the version upgrade operation. |

## Using the Event Objects

When you create an event handler, InfoPath creates the event handler's declaration in the project's form code file (FormCode.cs or FormCode.vb). In the declaration of the event handler, InfoPath uses **e** as the name of the parameter that is passed to the event handler. This parameter contains the event object that is associated with the event handler.
  
For example, when you create an event handler for the **OnLoad** event in design mode (by clicking **On Load Event** on the **Developer** tab), InfoPath adds the declaration for the event handler that receives the **DocReturnEvent** object to the form code file, and then opens the Code Editor so that you can add your code to the following event handler declaration.
  
```cs
// The following function handler is created by Microsoft Office 
// InfoPath. Do not modify the type or number of arguments.
[InfoPathEventHandler(EventType=InfoPathEventType.OnLoad)]
public void FormEvents_OnLoad(DocReturnEvent e)
{
   // Write your code here.
}
```

```vb
' The following function handler is created by Microsoft Office 
' InfoPath. Do not modify the type or number of arguments.
<InfoPathEventHandler(EventType:=InfoPathEventType.OnLoad)> _
Public Sub FormEvents_OnLoad(ByVal e As DocReturnEvent)
   ' Write your code here.
End Sub
```

When writing code for an event handler, you can use the properties and methods implemented by the event object that is passed through the **e** parameter. For example, in the following **OnBeforeChange** event handler, the [NewValue](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataDOMEvent.NewValue.aspx) property of the **DataDOMEvent** event object is used to check the value of the field that was just changed. If it is blank, the [ReturnMessage](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataDOMEvent.ReturnMessage.aspx) property of the **DataDOMEvent** event object is used to display an error to the user in a dialog box, and the [ReturnStatus](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataDOMEvent.ReturnStatus.aspx) property is set to **false**, indicating that the changes the user made should not be accepted.
  
```cs
[InfoPathEventHandler(MatchPath="/my:myFields/my:field1", 
    EventType=InfoPathEventType.OnBeforeChange)]
public void field1_OnBeforeChange(DataDOMEvent e)
{
   // Determine whether there is a new value.
   if ((string)e.NewValue == "")
   {
      // The value is blank, so display an error message and roll
      // back the changes.
      e.ReturnMessage = "You must supply a value for this field.";
      e.ReturnStatus = false;
      return;
   }
}
```

```vb
<InfoPathEventHandler(MatchPath:="/my:myFields/my:field1", _EventType:=InfoPathEventType.OnBeforeChange)> _
Public Sub field1_OnBeforeChange(ByVal e As DataDOMEvent)
   ' Determine whether there is a new value.
   If (e.NewValue = "") Then
      ' The value is blank, so display an error message and roll back
      ' the changes.
      e.ReturnMessage = "You must supply a value for this field."
      e.ReturnStatus = False
      Return
   End If
End Sub
```

> [!NOTE]
> Each of the InfoPath event objects in the InfoPath 2003-compatible object model implements different properties and methods. For more information about a particular event object, click the appropriate object in the Event Objects table shown earlier.
  