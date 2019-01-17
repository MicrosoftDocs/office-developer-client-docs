---
title: OnError macro action
TOCTitle: OnError macro action
ms:assetid: 5c6073c4-2c0f-0ed2-83b0-477636e2d81c
ms:mtpsurl: https://msdn.microsoft.com/library/Ff194562(v=office.15)
ms:contentKeyID: 48545088
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm62274
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# OnError macro action

**Applies to**: Access 2013, Office 2013

You can use the **OnError** action to specify what should happen when an error occurs in a macro.

## Setting

The **OnError** action has the following arguments.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Go to</p></td>
<td><p>Specify the general behavior that should occur when an error is encountered. Click the drop-down arrow and then click one of the following settings:</p>
<div class="tableSection">
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Setting</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Next</strong></p></td>
<td><p>Microsoft Office Access 2007 records the details of the error in the <strong>MacroError</strong> object but does not stop the macro. The macro continues with the next action.</p></td>
</tr>
<tr class="even">
<td><p><strong>Macro Name</strong></p></td>
<td><p>Access stops the current macro and runs the macro that is named in the <strong>Macro Name</strong> argument.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Fail</strong></p></td>
<td><p>Access stops the current macro and displays an error message.</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p>Macro Name</p></td>
<td><p>If the Go to argument is set to Macro Name, type the name of the macro to be used for error handling. The name you type must match a name in the <strong>Macro Name</strong> column of the current macro; you can't enter the name of a different macro object. In the example below, the <strong>ErrorHandler</strong> macro is contained in the same macro object as the <strong>OnError</strong> action. This argument must be left blank if the Go to argument is set to <strong>Next</strong> or <strong>Fail</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

- The **OnError** action is usually placed at the beginning of a macro, but you can also place the action later in the macro. The rules established by the action will take effect whenever the action is run.

- If you set the Go to argument to **Fail**, Access behaves the same way it would if there were no **OnError** action in the macro. That is, if an error is encountered, Access stops the macro and displays a standard error message. The main use for the **Fail** setting is to turn off any error handling that you established earlier in a macro.

## Example

The following macro demonstrates the use of the **OnError** action. In this example, the **OnError** action specifies that Access run a custom error handling macro named ErrorHandler when an error occurs. When an error occurs, the CatchErrors submacro is called. If the error number is 2102, a specific message is displayed and macro execution is halted. Otherwise, a message describing the error is displayed and the macro is paused so that you can perform additional troubleshooting. The ErrorHandler macro displays a message box that refers to the **MacroError** object to display information about the error.

**Sample code provided by** the [Microsoft Access 2010 Programmer’s Reference](https://www.amazon.com/Microsoft-Access-2010-Programmers-Reference/dp/8126528125).

```vb
    /* MACRO: mcrThrowErrors                                  */
    /* PURPOSE: Error handling using macros in Access 2010    */
    
    OnError
        Go to Macro Name
        Macro Name CatchErrors
    
    OpenForm 
        Form Name frmSamples
        View Form
        Filter Name
        Where Condition
        Data Mode
        Window Mode Normal
    
    MessageBox 
        Message This message appears after the OpenForm action
        Beep Yes
        Type None
        Title
    
    
    /* SUBMACRO: CatchErrors                                   */
    
    SubMacro: CatchErrors
        If [MacroError].[Number]=2101 Then
            MessageBox
                Message Cannot find the specified form!
                Beep Yes
                Type Critical
                Title
            StopMacro
    
        Else
            MessageBox
                Message =[MacroErro].[Description]
                Beep Yes
                Type None
                Title Unhandled Error
    
            SingleStep
        End If
    
    End SubMacro
```
