---
title: SetFilter macro action

TOCTitle: SetFilter macro action
ms:assetid: dee699e2-0840-1612-23ce-199ef8d30566
ms:mtpsurl: https://msdn.microsoft.com/library/Ff835438(v=office.15)
ms:contentKeyID: 48548203
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm122943
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# SetFilter macro action

**Applies to**: Access 2013, Office 2013

You can use the **SetFilter** action to apply a filter to the records in the active datasheet, form, report, or table.

## Setting

The **SetFilter** action has the following arguments.
|Action argument  |Description   |
|----------|-----------|
|Filter Name  |If provided, the name of a query or of a filter saved as a query. This argument or the WhereCondition argument is required in a client database. In a web database, this argument is not available.|
|Where Condition|If provided, a SQL WHERE clause that restricts the records in the datasheet, form, report, or table. In a web database, this argument is required.|
|Control Name|If provided, the name of the control that corresponds to the subform or subreport to be filtered. If empty, the current object is filtered.|


## Remarks

In a web database, the Where Condition argument cannot begin with an equal sign (=).

When you run this action, the filter is applied to the table, form, report or datasheet (for example, query result) that is active and has the focus.

The **Filter** property of the active object is used to save the WhereCondition argument and apply it at a later time. Filters are saved with the objects in which they are created. They are automatically loaded when the object is opened, but they are not automatically applied.

In a client database, to automatically apply a filter when the object is opened, set the **FilterOnLoad** property to True.

In a web database, to automatically apply a filter when the object is opened, add the **SetFilter** action to a macro, and add the macro to the object's **OnLoad** event.

## Example

The following example shows how to use the SetFilter action to filter the form in which the macro is defined.

**Sample code provided by** the [Microsoft Access 2010 Programmer’s Reference](https://www.amazon.com/Microsoft-Access-2010-Programmers-Reference/dp/8126528125).

```vb
    OpenForm
        Form Name sfrmFoods
        View Form
        Filter Name
        Where Condition
        Data Mode
        Window Mode Normal
    
    SetFilter
        Filter Name
        Where Condition =[display_name] Like "*cheese*"
        Control Name
```
