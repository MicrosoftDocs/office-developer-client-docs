---
title: "SetTempVar Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm150219
  
localization_priority: Normal
ms.assetid: 9c3b7bee-02c5-efbf-1276-4c4a1f7802d9
description: "You can use the SetTempVar action to create a temporary variable and set it to a specific value. The variable can then be used as a condition or argument in subsequent actions, or you can use the variable in another macro, in an event procedure, or on a form or report."
---

# SetTempVar Macro Action

You can use the **SetTempVar** action to create a temporary variable and set it to a specific value. The variable can then be used as a condition or argument in subsequent actions, or you can use the variable in another macro, in an event procedure, or on a form or report. 
  
## Setting

The **SetTempVar** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Name** <br/> |Enter the name of the temporary variable.  <br/> |
|**Expression** <br/> |Enter an expression that will be used to set the value for this temporary variable. Do not precede the expression with the equal ( **=** ) sign. You can click the **Build** button ![Formula](media/buildbut_ZA06047218.gif) to use the Expression Builder to set this argument.  <br/> |
   
## Remarks

- You can have up to 255 temporary variables defined at one time. If you do not remove a temporary variable, it will remain in memory until you close the database. It is a good practice to remove temporary variables when you are finished using them. To remove a single temporary variable, use the **[RemoveTempVar](removetempvar-macro-action.md)** action and set its argument to the name of the temporary variable that you want to remove. If you have more than one temporary variable and you want to remove them all at once, use the **RemoveAllTempVars** action. 
    
- Temporary variables are global. Once a temporary variable has been created, you can refer to it in an event procedure, a Visual Basic for Applications (VBA) module, a query, or an expression. For example, if you created a temporary variable named  *MyVar*  , you could use the variable as the control source for a text box by using the following syntax: 
    
  ```
  =[TempVars]![MyVar]
  ```

    > [!NOTE]
    > In macros, queries and event procedures, you do not need to precede the expression with an equal sign. 
  
    You can also refer to temporary variables in any add-ins or referenced databases.
    
- To run the **SetTempVar** action in a VBA module, use the **Add** method of the **TempVars** object. 
    
## Example

The following macro demonstrates how to create a temporary variable by using the **SetTempVar** action, then using the temporary variable in a condition and a message box, and then removing the temporary variable. 
  
|**Condition**|**Action**|**Arguments**|
|:-----|:-----|:-----|
||**SetTempVar** <br/> |**Name**: MyVar **Expression**: InputBox("Enter a non-zero number.")  <br/> |
|[TempVars]![MyVar]\<\>0  <br/> |**MessageBox** <br/> |**Message**: ="You entered " &amp; [TempVars]![MyVar] &amp; "." **Beep**: **Yes** **Type**: **Information** <br/> |
||**RemoveTempVar** <br/> |**Name**: MyVar  <br/> |
   

