---
title: "SetDisplayedCategories Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm20026
  
localization_priority: Normal
ms.assetid: e8bf39a6-c639-2232-7b21-3b0badf37e4b
description: "You can use the SetDisplayedCategories action to specify which categories are displayed under Navigate to Category in the title bar of the Navigation Pane. For example, if you want to prevent users from switching the Navigation Pane so that it displays objects sorted by Created Date, you can use this action to hide that option in the title bar's drop-down list."
---

# SetDisplayedCategories Macro Action

You can use the **SetDisplayedCategories** action to specify which categories are displayed under **Navigate to Category** in the title bar of the Navigation Pane. For example, if you want to prevent users from switching the Navigation Pane so that it displays objects sorted by **Created Date**, you can use this action to hide that option in the title bar's drop-down list.
  
## Setting

The **SetDisplayedCategories** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Show** <br/> |Select **Yes** to show the category or categories. Select **No** to hide them.  <br/> |
|**Category** <br/> |Enter or select the name of the category you want to show or hide. Leave blank to show or hide all categories.  <br/> |
   
## Remarks

- The caption in the title bar of the Navigation pane indicates which filter, if any, is currently active. Click anywhere in the bar to display the drop-down list. The items that this macro action controls are listed under **Navigate to Category**.
    
- This action only enables or disables the display of the specified category or categories; it does not perform any switching of the Navigation Pane display. For example, if you are displaying objects sorted by **Creation Date** and you use the **SetDisplayedCategories** action to disable the **Creation Date** option, Access does not switch the Navigation Pane to another category. 
    
- To run the **SetDisplayedCategories** action in a VBA module, use the **SetDisplayedCategories** method of the **DoCmd** object. 
    

