---
title: "OnError Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm62274
- vbaac10.chm62274
  
localization_priority: Normal
ms.assetid: 5c6073c4-2c0f-0ed2-83b0-477636e2d81c

description: "You can use the OnError action to specify what should happen when an error occurs in a macro."
---

# OnError Macro Action

You can use the **OnError** action to specify what should happen when an error occurs in a macro. 
  
## Setting

The **OnError** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Go to_ <br/> |Specify the general behavior that should occur when an error is encountered. Click the drop-down arrow and then click one of the following settings:  <br/> |**Setting**|**Description**|
|:-----|:-----|
|**Next** <br/> |Microsoft Office Access 2007 records the details of the error in the **MacroError** object but does not stop the macro. The macro continues with the next action.  <br/> |
|**Macro Name** <br/> |Access stops the current macro and runs the macro that is named in the **Macro Name** argument.  <br/> |
|**Fail** <br/> |Access stops the current macro and displays an error message.  <br/> |
   
|
| _Macro Name_ <br/> |If the  _Go to_ argument is set to  _Macro Name_, type the name of the macro to be used for error handling. The name you type must match a name in the **Macro Name** column of the current macro; you can't enter the name of a different macro object. In the example below, the **ErrorHandler** macro is contained in the same macro object as the **OnError** action. This argument must be left blank if the  _Go to_ argument is set to **Next** or **Fail**.  <br/> |
   
## Remarks

- The **OnError** action is usually placed at the beginning of a macro, but you can also place the action later in the macro. The rules established by the action will take effect whenever the action is run. 
    
- If you set the  _Go to_ argument to **Fail**, Access behaves the same way it would if there were no **OnError** action in the macro. That is, if an error is encountered, Access stops the macro and displays a standard error message. The main use for the **Fail** setting is to turn off any error handling that you established earlier in a macro. 
    
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
  

