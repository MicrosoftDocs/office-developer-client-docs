---
title: "Before Delete Macro Event"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm186077
  
localization_priority: Normal
ms.assetid: 1a8d3457-5c59-d13e-ada9-6ecd33dfd5b3
description: "The Before Delete event occurs when a record is deleted, but before the change is committed."
---

# Before Delete Macro Event

The **Before Delete** event occurs when a record is deleted, but before the change is committed. 
  
> [!NOTE]
> The **Before Delete** event is available only in Data Macros. 
  
## Remarks

Use the **Before Delete** event to perform any actions that you want to occur before a record is deleted. The **Before Change** is comonly used to perform validation and to raise custom error messges. 
  
You can use access a value in the record to be deleted by using the following syntax.
  
```
[Old].[Field Name ]
```

For example, to access the value of the QuantityInStock field in the record to be deleted, use the following syntax.
  
```
[Old].[QuantityInStock]
```

The values contained in the record to be deleted are deleted permanently when the **Before Delete** event ends. 
  
You can cancel the **Before Delete** event by using the **RaiseError** action. When an error is raised the changes contained in the **Before Delete** event are discarded. 
  
The following table lists macro commands that can be used in the **Before Delete** event. 
  
|**Command Type**|**Command**|
|:-----|:-----|
|Program Flow  <br/> |[Comment Macro Statement](comment-macro-statement.md) <br/> |
|Program Flow  <br/> |[Group Macro Statement](group-macro-statement.md) <br/> |
|Program Flow  <br/> |[If...Then...Else Macro Block](ifthenelse-macro-block.md) <br/> |
|Data Block  <br/> |[LookupRecord Macro Action](lookuprecord-data-block.md) <br/> |
|Data Action  <br/> |[ClearMacroError Macro Action](clearmacroerror-macro-action.md) <br/> |
|Data Action  <br/> |[OnError Macro Action](onerror-macro-action.md) <br/> |
|Data Action  <br/> |[RaiseError Macro Action](raiseerror-macro-action.md) <br/> |
|Data Action  <br/> |[SetLocalVar Macro Action](setlocalvar-macro-action.md) <br/> |
|Data Action  <br/> |[StopMacro Macro Action](stopmacro-macro-action.md) <br/> |
   
To create a Data macro that captures the **Before Delete** event, use the following steps. 
  
1. Open the table for which you want to capture the **Before Delete** event. 
    
2. On the **Table** tab, in the **Before Events** group, click **Before Delete**.
    

