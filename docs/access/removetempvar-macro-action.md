---
title: "RemoveTempVar Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm147125
  
localization_priority: Normal
ms.assetid: 7bcc5010-3e30-ecef-2c5d-a35e73c8e325
description: "You can use the RemoveTempVar action to remove a single temporary variable that you created by using the SetTempVar action."
---

# RemoveTempVar Macro Action

You can use the **RemoveTempVar** action to remove a single temporary variable that you created by using the **SetTempVar** action. 
  
## Setting

The **RemoveTempVar** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Name** <br/> |Enter the name of the temporary variable you want to remove.  <br/> |
   
## Remarks

- You can have up to 255 temporary variables defined at one time. If you do not remove a temporary variable, it will remain in memory until you close the database. It is a good practice to remove temporary variables when you are finished using them.
    
- Access automatically removes all temporary variables when you close the database or project.
    
- If you misspell the name of the variable to be removed, Access does not display an error. The variable you wanted to remove will remain in memory until you close the database.
    
- If you have created more than one temporary variable and you want to remove them all at once, use the **RemoveAllTempVars** action. 
    
- To run the **RemoveTempVar** action in a VBA module, use the **Remove** method of the **TempVars** object. 
    
## Example

The following macro demonstrates how to create a temporary variable, use it in a condition and a message box, and then remove the temporary variable by using the **RemoveTempVar** action. 
  
|**Condition**|**Action**|**Arguments**|
|:-----|:-----|:-----|
||**SetTempVar** <br/> |**Name**: MyVar **Expression**: InputBox("Enter a non-zero number.")  <br/> |
|[TempVars]![MyVar]\<\>0  <br/> |**MessageBox** <br/> |**Message**: ="You entered " &amp; [TempVars]![MyVar] &amp; "." **Beep**: **Yes** **Type**: **Information** <br/> |
||**RemoveTempVar** <br/> |**Name**: MyVar  <br/> |
   

