---
title: "SetReturnVar Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 53719857-00bb-4f33-b5d2-93aff92d736e
description: "The SetReturnVar action creates a return variable and sets it to a specific value."
---

# SetReturnVar Macro Action

The **SetReturnVar** action creates a return variable and sets it to a specific value. 
  
> [!NOTE]
> The **SetReturnVar** action is available only in Data Macros. 
  
## Setting

The **SetReturnVar** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
| _Name_ <br/> |Yes  <br/> |A string that specifies the name of the variable.  <br/> |
| _Expression_ <br/> |Yes  <br/> |An expression that will be used to set the value for this temporary variable. Do not precede the expression with the equal sign (=). You can click the **Build** button to use the **Expression Builder** to set this argument.  <br/> |
   
## Remarks

The **SetReturnVar** action is used to create a **ReturnVar**, which is variable that can be used by macros that call a data macro by using the **RunDataMacro** action. 
  
Once a **ReturnVar** is created by the **SetReturnVar** action, the calling macro can use it in an expression. For example, if you created a **ReturnVar** named **UpdateSuccess**, you could use the variable by using the following syntax:
  
```
=[ReturnVars]![UpdateSuccess]
```

The **SetReturnVar** action can be used only in named data macros. It is not available in data macros that are attached to a data macro event. 
  
## Example

The following example shows how to use the **SetReturnVar** action to return a value from a named data macro. A **ReturnVar** named **CurrentServiceRequest** is returned to the macro or Visual Basic for Applications (VBA) subroutine that called the named data macro. 
  
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
  

