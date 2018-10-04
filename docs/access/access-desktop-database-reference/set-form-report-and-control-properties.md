﻿---
title: Set form, report, and control properties
TOCTitle: Set form, report, and control properties
ms:assetid: 03349d86-f107-9e49-89df-62f55f3a0735
ms:mtpsurl: https://msdn.microsoft.com/library/Ff844789(v=office.15)
ms:contentKeyID: 48542977
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm12286
f1_categories:
- Office.Version=v15
---

# Set form, report, and control properties

**Applies to**: Access 2013 | Office 2013

Each form, report, section, and control has property settings that you can change to alter the look or behavior of that particular item. You view and change properties by using the property sheet, macro, or Visual Basic.

## Set properties

1. In form Design view or report Design view, select the control, section, form, or report for which you want to set the property. You can select:
    
   - One or more controls. To select multiple controls, hold down the SHIFT key and click the controls, or drag the mouse pointer over the controls you wish to select. If you select multiple controls, the property sheet will display only those properties that the selected controls have in common.
    
   - One section. Click the section selector of the section you wish to select.
    
   - The entire form or report. Click the form selector or report selector in the upper-left corner of the form or report.

2. Display the property sheet by right-clicking the object or section and then clicking **Properties** on the shortcut menu, or by clicking **Properties** on the toolbar.

3. Click the property for which you want to set the value, and then do one of the following:
    
   - In the property box, type the appropriate setting or expression.
    
   - If the property box contains an arrow, click the arrow and then click a value in the list.
    
   - If a **Build** button appears to the right of the property box, click it to display a builder or to display a dialog box giving you a choice of builders. For example, you can use the Code Builder, Macro Builder, or Query Builder to set some properties.

## Tips

- Microsoft Access provides a **Zoom** box for typing and viewing expressions or other long property settings. To display the **Zoom** box, click a property box in the property sheet. Then press SHIFT+F2, or right-click and then click **Zoom** on the shortcut menu.

- You can set the **ControlSource** property for some controls by typing the property setting in the control itself.

- You can change the default property settings for a type of control so that future controls you create will have the new default settings.

- The property settings of a bound control might not match the corresponding settings in the field in the underlying table or query to which the control is bound. If the settings are different, the form or report settings typically override those in the table or query. For more information about how properties are inherited, see How control properties relate to properties in their underlying fields.

