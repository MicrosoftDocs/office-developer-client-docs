---
title: ShowAllRecords Macro Action
TOCTitle: ShowAllRecords Macro Action
ms:assetid: 6f9741ad-0440-4b8d-abea-009063c111f8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff195587(v=office.15)
ms:contentKeyID: 48545538
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ShowAllRecords Macro Action


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Setting  
Remarks  
Example  

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

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Condition</p></th>
<th><p>Action</p></th>
<th><p>Arguments: Setting</p></th>
<th><p>Comment</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Company Name Filters] =1</p></td>
<td><p><strong>ApplyFilter</strong></p></td>
<td><p><strong>Where Condition</strong>: [Company Name] Like &quot;[AÀÁÂÃÄ]*&quot;</p></td>
<td><p>Filter for company names that start with A, À, Á, Â, Ã, or Ä.</p></td>
</tr>
<tr class="even">
<td><p>[Company Name Filters] =2</p></td>
<td><p><strong>ApplyFilter</strong></p></td>
<td><p><strong>Where Condition</strong>: [Company Name] Like &quot;B*&quot;</p></td>
<td><p>Filter for company names that start with B.</p></td>
</tr>
<tr class="odd">
<td><p>[Company Name Filters] =3</p></td>
<td><p><strong>ApplyFilter</strong></p></td>
<td><p><strong>Where Condition</strong>: [Company Name] Like &quot;[CÇ]*&quot;</p></td>
<td><p>Filter for company names that start with C or Ç.</p></td>
</tr>
<tr class="even">
<td><p>... Action rows for D through Y have the same format as A through C ...</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>[Company Name Filters] =26</p></td>
<td><p><strong>ApplyFilter</strong></p></td>
<td><p><strong>Where Condition</strong>: [Company Name] Like &quot;[ZÆØÅ]*&quot;</p></td>
<td><p>Filter for company names that start with Z, Æ, Ø, or Å.</p></td>
</tr>
<tr class="even">
<td><p>[Company Name Filters] =27</p></td>
<td><p><strong>ShowAllRecords</strong></p></td>
<td><p></p></td>
<td><p>Show all records.</p></td>
</tr>
<tr class="odd">
<td><p>[RecordsetClone].[RecordCount]&gt;0</p></td>
<td><p><strong>GoToControl</strong></p></td>
<td><p><strong>Control Name</strong>: CompanyName</p></td>
<td><p>If records are returned for the selected letter, move focus to the CompanyName control.</p></td>
</tr>
</tbody>
</table>

