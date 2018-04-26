---
title: "Submacro Macro Statement"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fb580c19-52cd-c0bd-9117-4fa721eead6b
description: "The Submacro statement defines a seperate macro in the Macro Designer window."
---

# Submacro Macro Statement

The **Submacro** statement defines a seperate macro in the Macro Designer window. 
  
## Setting

The **Submacro** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
| _Name_ <br/> |Yes  <br/> |A string that appears as the name of the macro.  <br/> |
   
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
  

