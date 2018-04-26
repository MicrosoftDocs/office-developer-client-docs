---
title: "WorkflowTasks Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm8454
  
localization_priority: Normal
ms.assetid: 4b299681-b45b-f6d1-2cfe-ebf01712bfc1
description: "You can use the WorkflowTasks action to display the Workflow Task dialog box."
---

# WorkflowTasks Macro Action

You can use the **WorkflowTasks** action to display the **Workflow Task** dialog box. 
  
## Setting

The **WorkflowTasks** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Record Number** <br/> |The position of the item in the Microsoft SharePoint Foundation list, starting with **1** for the first item in the list, **2** for the second item, and so on. You can also enter an expression for this argument.  <br/> |
   
## Remarks

- The **WorkflowTasks** action opens the **Workflow Tasks** dialog box. This dialog box displays all tasks that are available for the specified item. A workflow must be defined for the list in SharePoint Foundation. 
    
- The **WorkflowTasks** action can only be used after a linked SharePoint Foundation list has been opened and selected. To open and select the linked list, use the **OpenTable** action. If the list is already open, use the **SelectObject** action to select it. 
    
- The **WorkflowTasks** action has the same effect as right-clicking any cell in a linked SharePoint Foundation list while it is open in datasheet view, pointing to **Workflow**, and then clicking **Workflow Tasks**.
    
- To run the **WorkflowTasks** action in a VBA module, use the **WorkflowTasks** method of the **DoCmd** object. 
    

