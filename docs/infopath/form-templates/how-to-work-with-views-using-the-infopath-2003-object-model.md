---
title: "Work with Views Using the InfoPath 2003 Object Model"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
 
keywords:
- infopath 2003-compatible form templates, views,views [InfoPath 2007], InfoPath 2003-compatible form templates
 
ms.localizationpriority: medium
ms.assetid: feb1bfcb-1cb1-4d5c-bc84-df86a33a5934
description: "When working with an InfoPath form template, you can write code to access the form's views, and then perform a variety of actions on the data that the views contain. The InfoPath 2003-compatible object model supports access to a form's views through the use of the members of the ViewObject interface."
---

# Work with Views Using the InfoPath 2003 Object Model

When working with an InfoPath form template, you can write code to access the form's views, and then perform a variety of actions on the data that the views contain. The InfoPath 2003-compatible object model supports access to a form's views through the use of the members of the [ViewObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewObject.aspx) interface. 
  
## Overview of the ViewObject Interface

The [ViewObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewObject.aspx) interface provides the following methods and properties, which form developers can use to interact with an InfoPath view. 
  
> [!NOTE]
> The methods and properties of the [ViewObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewObject.aspx) interface are not available during the [OnLoad](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnLoad.aspx) event. 
  
|**Name**|**Description**|
|:-----|:-----|
|[DisableAutoUpdate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.DisableAutoUpdate.aspx) method  <br/> |Disables synchronization of the XML Document Object Model (DOM) and the view. |
|[EnableAutoUpdate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.EnableAutoUpdate.aspx) method  <br/> |Enables synchronization of the XML DOM and the view. |
|[ExecuteAction](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.ExecuteAction.aspx) method  <br/> |Executes an InfoPath editing action. |
|[Export](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.Export.aspx) method  <br/> |Exports the view as a file of the specified format. |
|[ForceUpdate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.ForceUpdate.aspx) method  <br/> |Synchronizes the XML DOM and the view. |
|[GetContextNodes](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.GetContextNodes.aspx) method  <br/> |Returns a reference to the [XMLNodesCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XMLNodesCollection.aspx) interface, based on the specified XML node and view context or on the current selection in the view. |
|[GetSelectedNodes](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.GetSelectedNodes.aspx) method  <br/> |Returns a reference to the **XMLNodesCollection** interface, based on the current selection in the view. |
|[SelectNodes](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.SelectNodes.aspx) method  <br/> |Selects a range of XML nodes in the view. |
|[SelectText](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.SelectText.aspx) method  <br/> |Selects the text contained in the specified XML node in the view. |
|[SwitchView](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.SwitchView.aspx) method  <br/> |Switches an InfoPath form to the specified view  <br/> |
|[Name](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.Name.aspx) property  <br/> |Returns a string value indicating the name of the current view. |
|[Window](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.Window.aspx) property  <br/> |Returns a reference to the [WindowObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.WindowObject.aspx) interface which accesses the **Window** associated with the view. |
   
> [!NOTE]
> The InfoPath 2003-compatible object model also provides the [ViewInfosCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewInfosCollection.aspx) interface, which can be used to get information about all of the views implemented in a form. 
  
## Using the ViewObject Interface

The [ViewObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewObject.aspx) interface is accessed through the [View](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.View.aspx) property of the [XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocument.aspx) interface (which is accessed through the `thisXDocument` variable that is initialized in the `_Startup` method of the form code class). For example, the following code sample demonstrates how to use the [Alert](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UI2.Alert.aspx) method of the [UIObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UIObject.aspx) interface to display a message box with the name of the current view that is associated with a form's underlying XML document. 
  
```cs
thisXDocument.UI.Alert("Current view name: " + 
   thisXDocument.View.Name);
```

```vb
thisXDocument.UI.Alert("Current view name: " &amp; _
   thisXDocument.View.Name)
```

All InfoPath forms contain at least one default view; however, InfoPath also supports the creation of multiple views of a form's underlying XML document. When you have multiple views in a form, the **View** object can be used to work with the view that is currently active. You can programmatically change the view that is currently active by using the **SwitchView** method of the **View** object, as the following code sample demonstrates. 
  
```cs
thisXDocument.View.SwitchView("MySecondView");
```

```vb
thisXDocument.View.SwitchView("MySecondView")
```

The previous example for switching a view will work only after the form is opened. To set a default view during the **OnLoad** event, use the [IsDefault](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewInfo.IsDefault.aspx) property of the [ViewInfoObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewInfoObject.aspx) interface, as shown in the following example. 
  
```cs
thisXDocument.ViewInfos["MyDefaultView"].IsDefault = true;
```

```vb
thisXDocument.ViewInfos("MyDefaultView").IsDefault = True
```


