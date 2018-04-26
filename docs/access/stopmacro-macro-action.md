---
title: "StopMacro Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6bbf9026-4536-43f2-aa43-3f2ecea01005
description: "You can use the StopMacro action to stop the currently running macro."
---

# StopMacro Macro Action

You can use the **StopMacro** action to stop the currently running macro. 
  
## Setting

The **StopMacro** action doesn't have any arguments. 
  
## Remarks

You typically use this action when a condition makes it necessary to stop the macro. You can use a conditional expression in the macro's action row that contains this action. When the expression evaluates to **True** (-1), Microsoft Access stops the macro. 
  
For example, you might create a macro that opens a form showing the daily order totals for the date entered in a custom dialog box. You could use a conditional expression to be sure that the **Order Date** control on the dialog box contains a valid date. If it doesn't, the **MessageBox** action can display an error message and the **StopMacro** action can stop the macro. 
  
If the macro has used the **Echo** or **SetWarnings** actions to turn echo or the display of system messages off, the **StopMacro** action automatically turns them back on. 
  
This action isn't available in a Visual Basic for Applications (VBA) module.
  
## Example

The following macro demonstrates the use of the **OnError** action. In this example, the **OnError** action specifies that Access run a custom error handling macro named **ErrorHandler** when an error occurs. When an error occurs, the **CatchErrors** submacro is called. If the error number is 2102, a specific message is displayed and macro execution is halted. Otherwise, a message describing the error is displayed and the macro is paused so that you can perform additional troubleshooting. The **ErrorHandler** macro displays a message box that refers to the **MacroError** object to display information about the error. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
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

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

