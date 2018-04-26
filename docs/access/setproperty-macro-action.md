---
title: "SetProperty Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm139044
  
localization_priority: Normal
ms.assetid: 58d2eac3-35b2-e9f8-47e0-62c9b52f2c24
description: "You can use the SetProperty action to set a property for a control on a form or a report."
---

# SetProperty Macro Action

You can use the **SetProperty** action to set a property for a control on a form or a report. 
  
## Setting

The **SetProperty** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Control Name_ <br/> |Type the name of the field or control for which you want to set the property value. Use only the control name, not the full syntax. Leave this argument blank to set the property for the current form or report.  <br/> |
| _Property_ <br/> |Select the property that you want to set. See the **Remarks** section in this article for a list of the properties that can be set by using this action.  <br/> |
| _Value_ <br/> |Type the value that the property is to be set to. For properties whose values are either Yes or No, use **-1** for Yes and **0** for No.  <br/> |
   
## Remarks

- You can use the **SetProperty** action to set the following properties of a control: **Enabled**, **Visible**, **Locked**, **Left**, **Top**, **Width**, **Height**, **Fore Color**, **Back Color**, or **Caption**. 
    
- If you enter an invalid value for the ** *Value* ** argument, no error occurs, but Access might change the property to a different value, depending on how it interprets the argument. 
    
- You can use the **SetProperty** action in a stand-alone macro only if you precede it with an action that selects the form or report containing the control for which you are setting the property. If the form or report is not open, you can use the **OpenForm** or **OpenReport** action to open and select it. If the form or report is already open, you can use the **SelectObject** action to select it. You can then use the **SetProperty** action to set the property. Selecting the object is not necessary if you use the **SetProperty** action in a macro which is embedded in a control on the same form or report as the control for which you are setting the property. 
    
- To run the **SetProperty** action in a VBA module, use the **SetProperty** method of the **DoCmd** object. 
    
## Example

The following example shows how to use the **SetProperty** action to toggle the visibility of the **MyTextBox** text box. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
Submacro: TestVisible
    SetProperty
        Control Name Text40
        Property Visible
        Value =Not[Text40].[Visible]
End Submacro
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

