---
title: "Walkthrough Creating and Debugging a Basic Form Template Using the InfoPath 2003 Object Model"
 
 
manager: soliver
ms.date: 1/13/2015
ms.audience: Developer
 
keywords:
- form templates [infopath 2007], walkthroughs,form templates [InfoPath 2007], creating InfoPath 2003-compatible,InfoPath 2003-compatible form templates, walkthroughs
 
localization_priority: Normal
ms.assetid: 7658705f-c062-49a1-bea6-837737df2425
description: "This topic provides a walkthrough of creating a basic InfoPath managed code form template that works with the InfoPath 2003-compatible object model provided by the Microsoft.Office.Interop.InfoPath.SemiTrust namespace."
---

# Walkthrough: Creating and Debugging a Basic Form Template Using the InfoPath 2003 Object Model

This topic provides a walkthrough of creating a basic InfoPath managed code form template that works with the InfoPath 2003-compatible object model provided by the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace. 
  
## Hello World

In the following example, you will learn how to display a simple alert dialog box by using the [Alert](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UI2.Alert.aspx) method of the InfoPath 2003-compatible object model. 
  
### Create a new InfoPath form template that works with the InfoPath 2003-compatible object model

1. Create a new form template that works with the InfoPath 2003-compatible object model, as described in [How to: Create a Form Template Using the InfoPath 2003 Object Model](how-to-create-a-form-template-using-the-infopath-2003-object-model.md).
    
2. Name the form template project HelloWorld and save it. 
    
    The project system creates code and project files, and then opens a blank form template in InfoPath design mode. You are now ready to add event handlers.
    
### Add a button with an OnClick event handler

1. In the **Controls** section on the **Home** tab, click the **Button** control to insert it into the view. 
    
2. Right-click the control, and then click **Button Properties**.
    
3. Change the **Label** to Alert.
    
4. Change the **ID** to AlertID.
    
5. Click **Edit Form Code**.
    
    An event handler skeleton for the [OnClick](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._ButtonEventSink_Event.OnClick.aspx) event is created and the focus moves to the code editor in Visual Studio 2012. For more information on working with event handlers, see [How to: Add an Event Handler Using the InfoPath 2003 Object Model](how-to-add-an-event-handler-using-the-infopath-2003-object-model.md). 
    
    You are now ready to add form code to the event handler for the button.
    
### Add form code to the event handler

1. In the **OnClick** event handler, type the following code: 
    
  ```cs
  thisXDocument.UI.Alert("Hello World!");
  ```

  ```VB.net
  thisXDocument.UI.Alert("Hello World!")
  ```

    Note that a Microsoft IntelliSense drop-down list is displayed after you type each period in the line of code. The entire event handler should look like the following:
    
  ```cs
  [InfoPathEventHandler(MatchPath="AlertID", EventType=InfoPathEventType.OnClick)]
  public void AlertID_OnClick(DocActionEvent e)
  {
      thisXDocument.UI.Alert("Hello World!");
  }
  ```

  ```VB.net
  <InfoPathEventHandler(MatchPath:="AlertID", EventType:=InfoPathEventType.OnClick)>
  Public Sub AlertID_OnClick(ByVal e As DocActionEvent)
      thisXDocument.UI.Alert("Hello World!")
  End Sub
  ```

    > [!NOTE]
    > As an alternative to using the **Alert** method, you can use the **MessageBox.Show** method of the **System.Windows.Forms** namespace to display a message box. To do so, you must add a reference to the System.Windows.Forms assembly, add  `using System.Windows.Forms;` or  `Imports System.Windows.Forms` to the directives at the beginning of your code file, and then type a line of code such as the following:  `MessageBox.Show("Hello World!); or MessageBox.Show("Hello World!)`
  
2. Switch to the InfoPath design mode window, and then click the **Preview** button on the **Home** tab. 
    
3. In the **Preview** window, click the **Alert** button. 
    
    A message box will be displayed with the text "Hello World!"
    
    The next procedure shows how to add debugging breakpoints to your form code.
    
### Debug form code

1. In the code editor, click the grey bar to the left of the line:
    
  ```cs
  thisXDocument.UI.Alert("Hello World!");
  ```

  ```VB.net
  thisXDocument.UI.Alert("Hello World!")
  ```

    A red circle is displayed and the line of code is highlighted to indicate that the runtime will pause at this breakpoint in your form code.
    
2. On the **Debug** menu, click **Start Debugging** (or press F5). 
    
3. In the InfoPath **Preview** window, click the **Alert** button. 
    
    The code editor is given focus, and the breakpoint line is highlighted.
    
4. On the **Debug** menu, click **Step Over** (or press Shift+F8) to continue stepping through the code. 
    
    The **Alert** method code is executed, and the "Hello World!" alert is displayed in the InfoPath **Preview** window. 
    
## Getting the Current User's Name

By using the .NET Framework classes, you can get access to functionality that was not easily available in script. In this example, you will learn how use the .NET Framework classes to retrieve the name of the current user.
  
### Add an OnLoad event handler

1. Open the InfoPath HelloWorld project that you created earlier.
    
2. On the **View** tab, click **Show Fields**.
    
3. Right-click the **myFields** node, and then click **Add**.
    
4. In **Name**, type **employee**, then click **OK**.
    
5. Drag the **employee** node into the view. 
    
6. On the **Developer** tab, click **On Load Event**.
    
    This will create an event handler for the [OnLoad](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnLoad.aspx) event, and focus moves to the code editor. The code in this event handler will be called each time the form is loaded. The next procedure shows how to add form code that retrieves the user's name to the event handler. 
    
### Add form code

1. In the **OnLoad** event handler, type the following code: 
    
  ```cs
  // Store an XML DOM node as a local variable.
  IXMLDOMNode nodeEmployee = thisXDocument.DOM.selectSingleNode("my:myFields/my:employee");
  if(nodeEmployee != null)
  {
      if(nodeEmployee.text == "")
      {
      // If the employee name is blank when the form is loaded, 
      // populate the employee node with the current user name.
      nodeEmployee.text = System.Environment.UserName;
      }
  }
  ```

  ```VB.net
  // Store an XML DOM node as a local variable.
  Dim nodeEmployee As IXMLDOMNode
  nodeEmployee = thisXDocument.DOM.selectSingleNode("my:myFields/my:employee");
  If Not(nodeEmployee Is Nothing) Then
      If(nodeEmployee.text = "") Then
      // If the employee name is blank when the form is loaded, 
      // populate the employee node with the current user name.
      nodeEmployee.text = System.Environment.UserName
      End If
  End If
  ```

2. Compile and preview the form.
    
    The employee text box should now be populated with your username. 
    
For information on how to deploy a managed code form template, see [How to: Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md). For information on the InfoPath object model and common programming tasks in managed code form templates that work with the InfoPath 2003-compatible object model, see [Understanding the InfoPath 2003 Object Model](understanding-the-infopath-2003-object-model.md). 
  
## See also

#### Concepts

[Initialization and Clean-up Code Using InfoPath 2003 Object Model](initialization-and-clean-up-code-using-infopath-2003-object-model.md)
  
[InfoPath 2003 Compatible Object Models](infopath-2003-compatible-object-models.md)
#### Other resources

[How to: Add an Event Handler Using the InfoPath 2003 Object Model](how-to-add-an-event-handler-using-the-infopath-2003-object-model.md)

