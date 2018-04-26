---
title: "ShowAllRecords Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6f9741ad-0440-4b8d-abea-009063c111f8
description: "You can use the ShowAllRecords action to remove any applied filter from the active table, query result set, or form, and display all records in the table or result set or all records in the form's underlying table or query."
---

# ShowAllRecords Macro Action

You can use the **ShowAllRecords** action to remove any applied filter from the active table, query result set, or form, and display all records in the table or result set or all records in the form's underlying table or query. 
  
## Setting

The **ShowAllRecords** action doesn't have any arguments. 
  
## Remarks

You can use this action to ensure that all records (including any changed or new records) are displayed for a table, query result set, or form. This action causes a requery of the records for a form or subform.
  
You can also use this action to remove any filter that was applied with the **ApplyFilter** action, the **Filter** command on the **Home** tab, or the **Filter Name** or **Where Condition** argument of the **OpenForm** action. 
  
This action has the same effect as clicking **Toggle Filter** on the **Home** tab, or right-clicking the filtered field and clicking **Clear filter from...** in Form view, Layout view, or Datasheet view. 
  
To run the **ShowAllRecords** action in a Visual Basic for Applications (VBA) module, use the **ShowAllRecords** method of the **DoCmd** object. 
  
## Example

 **Apply a filter by using a macro**
  
The following macro contains a set of actions, each of which filters the records for a Customer Phone List form. It shows the use of the **ApplyFilter**, **ShowAllRecords**, and **GoToControl** actions. It also shows the use of conditions to determine which toggle button in an option group has been selected on the form. Each action row is associated with a toggle button that selects the set of records starting with A, B, C, and so on, or all records. This macro should be attached to the **AfterUpdate** event of the CompanyNameFilter option group. 
  
|**Condition**|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|:-----|
|[Company Name Filters] =1  <br/> |**ApplyFilter** <br/> |**Where Condition**: [Company Name] Like "[AÀÁÂÃÄ]\*"  <br/> |Filter for company names that start with A, À, Á, Â, Ã, or Ä.  <br/> |
|[Company Name Filters] =2  <br/> |**ApplyFilter** <br/> |**Where Condition**: [Company Name] Like "B\*"  <br/> |Filter for company names that start with B.  <br/> |
|[Company Name Filters] =3  <br/> |**ApplyFilter** <br/> |**Where Condition**: [Company Name] Like "[CÇ]\*"  <br/> |Filter for company names that start with C or Ç.  <br/> |
| ... Action rows for D through Y have the same format as A through C ...  <br/> |
|[Company Name Filters] =26  <br/> |**ApplyFilter** <br/> |**Where Condition**: [Company Name] Like "[ZÆØÅ]\*"  <br/> |Filter for company names that start with Z, Æ, Ø, or Å.  <br/> |
|[Company Name Filters] =27  <br/> |**ShowAllRecords** <br/> ||Show all records.  <br/> |
|[RecordsetClone].[RecordCount]\>0  <br/> |**GoToControl** <br/> |**Control Name**: CompanyName  <br/> |If records are returned for the selected letter, move focus to the CompanyName control.  <br/> |
   

