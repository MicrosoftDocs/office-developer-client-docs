---
title: "SetFilter Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm122943
  
localization_priority: Normal
ms.assetid: dee699e2-0840-1612-23ce-199ef8d30566
description: "You can use the SetFilter action to apply a filter to the records in the active datasheet, form, report, or table."
---

# SetFilter Macro Action

You can use the **SetFilter** action to apply a filter to the records in the active datasheet, form, report, or table. 
  
## Setting

The **SetFilter** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Filter Name_ <br/> |If provided, the name of a query or of a filter saved as a query. This argument or the  _WhereCondition_ argument is required in a client database. In a Web database, this argument is not available.  <br/> |
| _Where Condition_ <br/> |If provided, a SQL WHERE clause that restricts the records in the datasheet, form, report, or table. In a Web database, this argument is required.  <br/> |
| _Control Name_ <br/> |If provided, the name of the control that corresponds to the subform or subreport to be filtered. If empty, the current object is filtered.  <br/> |
   
## Remarks

In a web database, the  _Where Condition_ argument cannot begin with an equal sign (=). 
  
When you run this action, the filter is applied to the table, form, report or datasheet (for example, query result) that is active and has the focus.
  
The **Filter** property of the active object is used to save the  _WhereCondition_ argument and apply it at a later time. Filters are saved with the objects in which they are created. They are automatically loaded when the object is opened, but they are not automatically applied. 
  
In a client database, to automatically apply a filter when the object is opened, set the **FilterOnLoad** property to **True**.
  
In a web database, to automatically apply a filter when the object is opened, add the **SetFilter** action to a macro, and add the macro to the object's **OnLoad** event. 
  
## Example

The following example shows how to use the **SetFilter** action to filter the form in which the macro is defined. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
OpenForm
    Form Name sfrmFoods
    View Form
    Filter Name
    Where Condition
    Data Mode
    Window Mode Normal
SetFilter
    Filter Name
    Where Condtion =[display_name] Like "*cheese*"
    Control Name
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

