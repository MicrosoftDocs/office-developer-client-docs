---
title: "SetLocalVar Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm176660
- vbaac10.chm176660
  
localization_priority: Normal
ms.assetid: 8a6af395-0f76-72e2-37f3-2cff22a38b3c
description: "The SetLocalVar action creates a temporary variable and set it to a specific value."
---

# SetLocalVar Macro Action

The **SetLocalVar** action creates a temporary variable and set it to a specific value. 
  
## Setting

The **SetLocalVar** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |Yes  <br/> |A string that specifies the name of the variable.  <br/> |
|**Expression** <br/> |Yes  <br/> |An expression that will be used to set the value for this temporary variable. Do not precede the expression with the equal sign (=). You can click the **Build** button to use the **Expression Builder** to set this argument.  <br/> |
   
## Remarks

Variables created by the **SetLocalVar** action can be used only in the macro in which they are defined. Use the **[SetTempVar](settempvar-macro-action.md)** action to define a variable that can be used in another macro, in an event procedure, or on a form or report. 
  
Once a temporary variable has been created, you can refer to it in an expression. For example, if you created a temporary variable named TotalAmount, you could use the variable as the control source for a text box by using the following syntax.
  
```
=[LocalVars]![TotalAmount]
```

> [!NOTE]
> In a Data Macro, you do not have to use the LocalVars collection to refer to a variable. For example, if you created a temporary variable in a Data Macro named TotalAmount, you could use the variable as the control source for a text box by using the following syntax
  
 `=[TotalAmount]`
  

