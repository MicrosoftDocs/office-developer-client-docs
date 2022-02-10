---
title: "Shape Data Row (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251344
 
ms.localizationpriority: medium
ms.assetid: f3a83496-fccc-9d6a-02b9-60ebaf4911ea
description: "Contains the information for a single shape data item associated with a shape. A shape contains one Shape Data row for each shape data item.Shape Data rows are named Prop.name and contain the following cells. For more details, see the specific cell topics."
---

# Shape Data Row (Shape Data Section)

Contains the information for a single shape data item associated with a shape. A shape contains one Shape Data row for each shape data item.Shape Data rows are named Prop.name and contain the following cells. For more details, see the specific cell topics.
  
|**Cell**|**Description**|
|:-----|:-----|
|[Label](label-cell-shape-data-section.md) <br/> |Specifies the label that appears to users in the **Shape Data** dialog box or window. |
|[Prompt](prompt-cell-shape-data-section.md) <br/> |Specifies descriptive or instructional text that appears to users in the **Shape Data** dialog box or window when the item is selected. |
|[Type](type-cell-shape-data-section.md) <br/> |Specifies a data type for the shape data item value: string (0), a fixed list (1), a number (2), a Boolean value (3), a variable list (4), a date or time (5), a duration (6), or a currency (7). |
|[Format](format-cell-shape-data-section.md) <br/> |Specifies the formatting of a shape data item. |
|[Value](value-cell-shape-data-section.md) <br/> |Contains the item's value as entered in the **Shape Data** dialog box or window. |
|[SortKey](sortkey-cell-shape-data-section.md) <br/> |Specifies a key by which items in the **Shape Data** dialog box or window are listed. |
|[Invisible](invisible-cell-shape-data-section.md) <br/> |Specifies whether the shape data item is visible in the **Shape Data** dialog box or window. TRUE = not visible; FALSE = visible. |
|[Ask](ask-cell-shape-data-section.md) <br/> |Determines whether a user is queried to enter shape data information for a shape when an instance is created or the shape is duplicated or copied. |
|[LangID](langid-cell-shape-data-section.md) <br/> |Specifies the language in which to display the shape data item value. |
|[Calendar](calendar-cell-miscellaneous-section.md) <br/> |Specifies the type of calendar used when the Type of a shape data item is Date. |
   
## Remarks

 You can add as many Prop.  *name*  rows as you need, assign meaningful names to the rows, and set cell values. To add a shape data item to an existing Shape Data section, right-click a row and click **Insert Row** on the shortcut menu. 
  
You can reference these cells by their row name, which appears in a ShapeSheet window in red text. To assign meaningful names to Prop. *name*  rows, click the row, and then type a name such as  *Price*  , for example, to create the row name Prop.Price. You can then reference the Label cell by using Prop.Price.Label. 
  
The row name you enter must be unique within the section.
  

