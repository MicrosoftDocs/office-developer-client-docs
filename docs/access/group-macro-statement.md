---
title: "Group Macro Statement"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 42aa4afa-ab5d-9dcc-2182-786f025e316d
description: "The Group statement enables you to specify a block of actions within a macro that you can expand or collapse."
---

# Group Macro Statement

The **Group** statement enables you to specify a block of actions within a macro that you can expand or collapse. 
  
## Setting

The **Group** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
|**Description** <br/> |No  <br/> |A string that appears as the title of a group when it is collapsed.  <br/> |
   
## Remarks

The **Group** statment does not define a region of a macro that can be executed separately. Use the **[Submacro](submacro-macro-statement.md)** statment to define a set of actions to be executed separately in the **Macro Designer** window. 
  

