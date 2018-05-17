---
title: "Log Values to a Field for Debugging"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 5874dc28-1b10-48a3-8287-9474db0b7435
description: "When debugging an InfoPath form template, it is often useful to log values directly into a field in the form to create a record of debug data during a session of testing the form. The following procedures show how to create a multi-line field, and then add helper functions to the form code that enable you log debug data into that field."
---

# Log Values to a Field for Debugging

When debugging an InfoPath form template, it is often useful to log values directly into a field in the form to create a record of debug data during a session of testing the form. The following procedures show how to create a multi-line field, and then add helper functions to the form code that enable you log debug data into that field.
  
### To create a multi-line text field

1. Add a **Text Box** control to the form, and then resize it so that it can display multiple lines. 
    
2. Right-click the text box, click **Text Box Properties**, and then click the **Multi-line** check box on the **Display** tab. 
    
### To add helper functions to log debug information to the field

1. On the **Developer** tab, click **Code Editor**, and then save the form template if you are prompted.
    
2. In the Code Editor, add the following three helper functions to the public class in the form code file.
    
    > [!IMPORTANT]
    > Make sure that you update the value set for the  `debugFieldXpath` variable in the  `AddToDebugField` function to the correct XPath expression for the field bound to the control that you created in the first procedure. 
  
  ```cs
  private void AddToDebugField(string valueToAdd)
  {
      // Update the value of debugFieldXpath to the XPath of the
      // multi-line field where you want to log debug information.
      string debugFieldXpath = "/my:myFields/my:field1";
      string headerLine = "----------------- " + DateTime.Now + 
          " -----------------" + "\r\n";
      SetDebugFieldValue(debugFieldXpath, headerLine + valueToAdd + 
          "\r\n" + GetDebugFieldValue(debugFieldXpath));
  }
  private string GetDebugFieldValue(string xpath)
  {
      return this.CreateNavigator().SelectSingleNode(xpath, 
          this.NamespaceManager).Value;
  }
  private void SetDebugFieldValue(string xpath, string value)
  {
      this.CreateNavigator().SelectSingleNode(xpath, 
          this.NamespaceManager).SetValue(value);
  }
  ```

  ```VB.net
  Private Sub AddToDebugField(ByVal valueToAdd As String)
      ' Update the value of debugFieldXpath to the XPath of the 
      ' multi-line field where you want to log debug information.
      Dim debugFieldXpath As String = "/my:myFields/my:field1"
      Dim headerLine As String = "----------------- " _
          &amp; DateTime.Now &amp; " -----------------" &amp; vbCrLf
      SetDebugFieldValue(debugFieldXpath, (headerLine &amp; valueToAdd &amp; vbCrLf) _
          &amp; GetDebugFieldValue(debugFieldXpath))
  End Sub
  Private Function GetDebugFieldValue(ByVal xpath As String) As String
      Return Me.CreateNavigator().SelectSingleNode(xpath, _
          Me.NamespaceManager).Value
  End Function
  Private Sub SetDebugFieldValue(ByVal xpath As String, ByVal value As String)
      Me.CreateNavigator().SelectSingleNode(xpath, _
          Me.NamespaceManager).SetValue(value)
  End Sub
  ```

    > [!VISUAL BASIC NOTE]
    > When using Visual Basic, add  `Imports Microsoft.VisualBasic.Constants` to the directives at the top of the form code file. 
  
### To test the AddToDebugField function

1. On the **Developer** tab, click **Loading Event**, and then add the following line of code to the event handler.
    
  ```cs
  AddToDebugField("Form loaded");
  ```

  ```VB.net
  AddToDebugField("Form loaded")
  ```

2. On the **Developer** tab, click **View Switched Event**, and then add the following line of code to the event handler.
    
  ```cs
  AddToDebugField("View switched: " + this.CurrentView.ViewInfo.Name);
  ```

  ```VB.net
  AddToDebugField("View switched: " &amp; Me.CurrentView.ViewInfo.Name)
  ```

3. On the **Home** tab, click **Preview**.
    
The debug field should display two entries: one indicating that the form is loaded, and another indicating the name of the view. These examples use event handlers for events that occur as the form is opened. However, after the form is loaded, you can call the  `AddToDebugField` function from other event handlers in addition to any other code running in the context of the form. 
  

