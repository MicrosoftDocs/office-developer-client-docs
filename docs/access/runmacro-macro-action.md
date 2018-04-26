---
title: "RunMacro Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm43195
  
localization_priority: Normal
ms.assetid: 25966f20-8160-0821-b88a-ed08b7786fdc
description: "You can use the RunMacro action to run a macro. The macro can be in a macro group."
---

# RunMacro Macro Action

You can use the **RunMacro** action to run a macro. The macro can be in a macro group. 
  
You can use this action:
  
- To run a macro from within another macro.
    
- To run a macro based on a certain condition.
    
- To attach a macro to a custom menu command.
    
## Setting

The **RunMacro** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Macro Name** <br/> |The name of the macro to run. The **Macro Name** box in the **Action Arguments** section of the Macro Builder pane shows all macros (and macro groups) in the current database. If the macro is in a macro group, it's listed under the macro group name in the list as  *macrogroupname*  .  *macroname*  . This is a required argument. If you run a macro containing the **RunMacro** action in a library database, Microsoft Access looks for the macro with this name in the library database and doesn't look for it in the current database.  <br/> |
|**Repeat Count** <br/> |The maximum number of times the macro will run. If you leave this argument blank (and the **Repeat Expression** argument is also blank), the macro runs once.  <br/> |
|**Repeat Expression** <br/> |An expression that evaluates to **True** (-1) or **False** (0). The macro stops running if the expression evaluates to **False**. The expression is evaluated each time the macro runs.  <br/> |
   
## Remarks

If you enter a macro group name for the **Macro Name** argument, Access runs the first macro in the macro group. 
  
This action is similar to clicking **Run Macro** on the **Database Tools** tab, selecting a macro, and clicking **OK**. However, this command runs the macro only once, whereas the **RunMacro** action can run a macro as many times as you want. 
  
> [!TIP]
> You can use the **Repeat Count** and **Repeat Expression** arguments to determine how many times the macro runs: 
  
- If you leave both arguments blank, the macro runs once.
    
- If you enter a number for **Repeat Count** but leave **Repeat Expression** blank, the macro runs the specified number of times. 
    
- If you leave **Repeat Count** blank but enter an expression for **Repeat Expression**, the macro runs until the expression evaluates to **False**.
    
- If you enter values for both arguments, the macro runs the number of times specified in **Repeat Count** or until **Repeat Expression** evaluates to **False**, whichever occurs first.
    
When you run a macro containing the **RunMacro** action, and it reaches the **RunMacro** action, Access runs the called macro. When the called macro has finished, Access returns to the original macro and runs the next action. 
  
> [!NOTE]
>  You can call a macro in the same macro group or in another macro group. >  You can nest macros. That is, you can run macro A, which in turn calls macro B, and so on. In each case, when the called macro has finished, Access returns to the macro that called it and runs the next action in that macro. 
  
To run the **RunMacro** action in a Visual Basic for Applications (VBA) module, use the **RunMacro** method of the **DoCmd** object. 
  

