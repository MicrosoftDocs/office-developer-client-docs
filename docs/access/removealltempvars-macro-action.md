---
title: "RemoveAllTempVars Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm117413
  
localization_priority: Normal
ms.assetid: 409fd836-4a53-cefd-4264-8cee0fa8ac52
description: "You can use the RemoveAllTempVars action to remove any temporary variables that you created by using the SetTempVar action."
---

# RemoveAllTempVars Macro Action

You can use the **RemoveAllTempVars** action to remove any temporary variables that you created by using the **SetTempVar** action. 
  
## Setting

The **RemoveAllTempVars** action does not have any arguments. 
  
## Remarks

- You can have up to 255 temporary variables defined at one time. If you do not remove a temporary variable, it will remain in memory until you close the database or project. It is a good practice to remove temporary variables when you are finished using them.
    
- Access automatically removes all temporary variables when you close the database or project.
    
- To remove a single temporary variable, use the **RemoveTempVar** action and set its argument to the name of the temporary variable you want to remove. 
    
- To run the **RemoveAllTempVars** action in a VBA module, use the **RemoveAll** method of the **TempVars** object. 
    
## Example

The following macro demonstrates how to create a temporary variable, use it in a condition and a message box, and then remove the temporary variable by using the **RemoveAllTempVars** action. 
  
|**Condition**|**Action**|**Arguments**|
|:-----|:-----|:-----|
||**SetTempVar** <br/> |**Name**: MyVar **Expression**: InputBox("Enter a non-zero number.")  <br/> |
|[TempVars]![MyVar]\<\>0  <br/> |**MessageBox** <br/> |**Message**: ="You entered " &amp; [TempVars]![MyVar] &amp; "." **Beep**: **Yes** **Type**: **Information** <br/> |
||**RemoveAllTempVars** <br/> ||
   

