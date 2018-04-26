---
title: "LockNavigationPane Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm172454
  
localization_priority: Normal
ms.assetid: abf7a989-c7cf-3efa-8df4-3c5b075d0e5f
description: "You can use the LockNavigationPane action to prevent users from deleting database objects that are displayed in the Navigation Pane."
---

# LockNavigationPane Macro Action

You can use the **LockNavigationPane** action to prevent users from deleting database objects that are displayed in the Navigation Pane. 
  
## Setting

The **LockNavigationPane** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Lock** <br/> |Select **Yes** to lock the Navigation Pane, or **No** to unlock the Navigation Pane.  <br/> |
   
## Remarks

Locking the Navigation Pane prevents you from deleting database objects or cutting database objects to the clipboard. It does  *not*  prevent you from performing any of the following operations: 
  
- Copying database objects to the clipboard
    
- Pasting database objects from the clipboard
    
- Displaying or hiding the Navigation Pane
    
- Selecting different Navigation Pane organization schemes
    
- Showing or hiding sections of the Navigation Pane
    
To run the **LockNavigationPane** action in a VBA module, use the **LockNavigationPane** method of the **DoCmd** object. 
  

