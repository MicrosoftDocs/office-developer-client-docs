---
title: "OpenTable Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm149011
  
localization_priority: Normal
ms.assetid: 4220ad3a-d064-0034-2806-ec1a447cebac
description: "You can use the OpenTable action to open a table in Datasheet view, Design view, or Print Preview. You can also select a data entry mode for the table."
---

# OpenTable Macro Action

You can use the **OpenTable** action to open a table in Datasheet view, Design view, or Print Preview. You can also select a data entry mode for the table. 
  
## Setting

The **OpenTable** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Table Name** <br/> |The name of the table to open. The **Table Name** box in the **Action Arguments** section of the Macro Builder pane shows all tables in the current database. This is a required argument. If you run a macro containing the **OpenTable** action in a library database, Microsoft Microsoft Access looks for the table with this name first in the library database, then in the current database.  <br/> |
|**View** <br/> |The view in which the table will open. Click **Datasheet**, **Design**, **Print Preview**, **PivotTable**, or **PivotChart** in the **View** box. The default is **Datasheet**.  <br/> |
|**Data Mode** <br/> |The data entry mode for the table. This applies only to tables opened in Datasheet view. Click **Add** (the user can add new records but can't edit existing records), **Edit** (the user can edit existing records and add new records), or **Read Only** (the user can only view records). The default is **Edit**.  <br/> |
   
## Remarks

This action is similar to double-clicking the table in the Navigation Pane, or right-clicking the table in the Navigation Pane and selecting a view.
  
> [!TIP]
> You can drag a table from the Navigation Pane to a macro action row. This automatically creates an **OpenTable** action that opens the table in Datasheet view. 
  
To run the **OpenTable** action in a Visual Basic for Applications (VBA) module, use the **OpenTable** method of the **DoCmd** object. 
  

