---
title: "RunDataMacro Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm168493
  
localization_priority: Normal
ms.assetid: fe4ac2f4-7851-7797-ce91-5f2dd3ba4d22
description: "You can use the RunDataMacro action to run a named data macro."
---

# RunDataMacro Macro Action

You can use the **RunDataMacro** action to run a named data macro. 
  
## Setting

The **RunDataMacro** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Name_ <br/> |The name of the data macro to run.  <br/> |
   
## Remarks

You can use the **RunDataMacro** action in macros, named data macros, and the following macro events: **[After Delete Macro Event](after-delete-macro-event.md)**, **[After Insert Macro Event](after-insert-macro-event.md)** and **[After Update Macro Event](after-update-macro-event.md)**. 
  
The name of the data macro must include the table to which it is attached (for example, **Comments.AddComment**, not just **AddComment**).
  
When you select the data macro that you want to run in the macro designer, Access determines if the data macro requires parameters. If the data macro requires parameters, text boxes appear where you can type in the arguments.
  
When you run a macro that contains the **RunDataMacro** action and it reaches the **RunDataMacro** action, Access runs the called data macro. When the called data macro has finished, Access returns to the original macro and runs the next action. 
  
## Example

The following example shows how to pass a parameter to a named data macro. The **dmGetCurrentServiceRequest** data macro of the **tblServiceRequests** table is called by using the **RunDataMacro** action. When the **dmGetCurrentServiceRequest** is finished, the **CurrentServiceRequest** variable returned form the data macro is written to the **txtCurrentSR text** box. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
RunDataMacro
    Macro Name tblServiceRequests.dmGetCurrentServiceRequest
Parameters
    prmAssignedTo =[ID]
SetProperty
    Control Name txtCurrentSR
    Property Value
    Value =[ReturnVars]![CurrentServiceRequest]
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

