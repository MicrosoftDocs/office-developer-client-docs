---
title: "If...Then...Else Macro Block (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 18d28dc1-c41f-47c6-b5c7-258d5f877d01
description: "You can use the If macro block to conditionally execute a group of actions, depending on the value of an expression."
---

# If...Then...Else Macro Block (Access custom web app)

You can use the **If** macro block to conditionally execute a group of actions, depending on the value of an expression. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

```
IfexpressionThen 
 Insert macro actions here ... 
Else Ifexpression  
 Insert macro actions here ... 
Else 
 Insert macro actions here ... 
End If
```

## Setting

For both **If** and ** Else If **, the following arguments are required. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Expression** <br/> |The condition that you wish to test. It must be an expression that evaluates to True or False.  <br/> |
   
## Remarks

When you select the **If** macro block, a textbox appears so that you can enter an expression that represents the condition you wish to test. In addition, a combo box appears where you can insert a macro action, below which the text "End If" automatically displays. The If and the End If bracket an area in which you can enter a group, or block, of actions. The block executes only if the expression that you enter is True. 
  
To evaluate a different expression when the first expression is false, you can click **Add Else If** to insert an optional **Else If** block. You must enter an expression that evaluates to True or False. In this case, the block executes only if the expression is True and the first expression is False. 
  
You can add as many **Else If** blocks as you like to an If block. 
  
You can click **Add Else** to insert an optional **Else** block. In this case, the actions that you insert below the **Else** form the **Else** block, which executes only when the actions above do not. You can add a single **Else** block to an **If** block. 
  
In the following code example, the macro actions in the first block execute if the value of [Status] is greater than 0. If the value of [Status] is not greater than 0, the expression that follows the **Else If** is evaluated. The macro actions in the **Else If** block execute if the value of [Status] is equal to 0. Finally, if neither the first block nor the second block execute, the actions in the **Else** block execute. 
  
```
If[Status] > 0Then 
 Insert macro actions here ... 
Else If[Status] = 0  
 Insert macro actions here ... 
Else 
 Insert macro actions here ... 
End If
```

You can nest **If** blocks. You should consider nesting an **If** block within an **If** block if you want to evaluate a second expression when the first expression is True. In the following code example, the inner **If** block only executes when the value of [Status] is both greater than 0  *and*  greater than 100. 
  

