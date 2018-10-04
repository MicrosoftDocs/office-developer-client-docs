---
title: SearchForRecord Macro Action
TOCTitle: SearchForRecord Macro Action
ms:assetid: a3483c41-adb5-5923-55f4-1a3c4f60cb2f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff821023(v=office.15)
ms:contentKeyID: 48546781
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm118713
f1_categories:
- Office.Version=v15
---

# SearchForRecord Macro Action


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Setting  
Remarks  
Example  

You can use the **SearchForRecord** action to search for a specific record in a table, query, form or report.

## Setting

The **SearchForRecord** action has the following arguments.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Object Type</strong></p></td>
<td><p>Enter or select the type of database object that you are searching in. You can select <strong>Table</strong>, <strong>Query</strong>, <strong>Form</strong>, or <strong>Report</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Object Name</strong></p></td>
<td><p>Enter or select the specific object that contains the record to search for. The drop-down list shows all database objects of the type you selected for the <strong>Object Type</strong> argument.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Record</strong></p></td>
<td><p>Specify the starting point and direction of the search.</p>
<div class="tableSection">
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Setting</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Previous</strong></p></td>
<td><p>Search backward from the current record.</p></td>
</tr>
<tr class="even">
<td><p><strong>Next</strong></p></td>
<td><p>Search forward from the current record.</p></td>
</tr>
<tr class="odd">
<td><p><strong>First</strong></p></td>
<td><p>Search forward from the first record. This is the default value for this argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>Last</strong></p></td>
<td><p>Search backward from the last record.</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>Where Condition</strong></p></td>
<td><p>Enter the criteria for the search using the same syntax as an SQL WHERE clause, only without the word &quot;WHERE&quot;. For example,</p>
<pre><code>Description = &quot;Beverages&quot;</code></pre>
<p>To create a criterion that includes a value from a text box on a form, you must create an expression that concatenates the first part of the criterion with the name of the text box containing the value for which to search. For example, the following criterion will search the Description field for the value in the text box named txtDescription on the form named frmCategories. Note the equal sign (<strong>=</strong>) at the beginning of the expression, and the use of single quotation marks (<strong>'</strong>) on either side of the text box reference:</p>
<pre><code>=&quot;Description = &#39;&quot; &amp; Forms![frmCategories]![txtDescription] &amp; &quot;&#39;&quot;</code></pre></td>
</tr>
</tbody>
</table>


## Remarks

  - In cases where more than one record matches the criteria in the **Where Condition** argument, the following factors determine which record is found:
    
      - **The Record argument setting**See the table in the Settings section for more information about the **Record** argument.
    
      - **The sort order of the records**For example, if the **Record** argument is set to **First**, changing the sort order of the records might change which record is found.

  - The object specified in the **Object Name** argument must be open before this action is run. Otherwise, an error occurs.

  - If the criteria in the **Where Condition** argument are not met, no error occurs and the focus remains on the current record.

  - When searching for the previous or next record, the search does not "wrap" when it reaches the end of the data. If there are no further records that match the criteria, no error occurs and the focus remains on the current record. To confirm that a match was found, you can enter a condition for the next action, and make the condition the same as the criteria in the **Where Condition** argument.

  - To run the **SearchForRecord** action in a VBA module, use the **SearchForRecord** method of the **DoCmd** object.

  - The **SearchForRecord** action is similar to the **[FindRecord](findrecord-macro-action.md)** action, but **SearchForRecord** has more powerful search features. The **FindRecord** action is primarily used for finding strings, and it duplicates the functionality of the **Find** dialog box. The **SearchForRecord** action uses criteria that are more like those of a filter or an SQL query. The following list demonstrates some things you can do with the **SearchForRecord** action:
    
      - You can use complex criteria in the **Where Condition** argument, such as
        
            Description = "Beverages" and CategoryID = 11
    
      - You can refer to fields that are in the record source of a form or report but aren't displayed on the form or report. In the preceding example, neither Description nor CategoryID must be displayed on the form or report for the criteria to work.
    
      - You can use logical operators, such as **\<**, **\>**, **AND**, **OR**, and **BETWEEN**. The **FindRecord** action only matches strings that equal, start with, or contain the string being searched for.

## Example

The following macro first opens the Categories table by using the **OpenTable** action. The macro then uses the **SearchForRecord** action to find the first record in the table where the Description field equals "Beverages."

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action</p></th>
<th><p>Arguments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>OpenTable</strong></p></td>
<td><p><strong>Table Name</strong>: Categories<strong>View</strong>: <strong>DatasheetData Mode</strong>: <strong>Edit</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>SearchForRecord</strong></p></td>
<td><p><strong>Object Type</strong>: <strong>TableObject Name</strong>: Categories<strong>Record</strong>: <strong>FirstWhere Condition</strong>: Description = &quot;Beverages&quot;</p></td>
</tr>
</tbody>
</table>

