---
title: OpenReport Macro Action
TOCTitle: OpenReport Macro Action
ms:assetid: cd35faf2-190d-ac48-cf59-81c1599eb764
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff834462(v=office.15)
ms:contentKeyID: 48547758
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm188079
f1_categories:
- Office.Version=v15
---

# OpenReport Macro Action


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Setting  
Remarks  
Example  
About the Contributors  

You can use the **OpenReport** action to open a report in Design view or Print Preview, or to send the report directly to the printer. You can also restrict the records that are printed in the report.

## Setting

The **OpenReport** action has the following arguments.

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
<td><p>Report Name</p></td>
<td><p>The name of the report to open. The <strong>Report Name</strong> box in the <strong>Action Arguments</strong> section of the <strong>Macro Builder</strong> pane shows all reports in the current database. This is a required argument. If you run a macro containing the OpenReport action in a library database, Microsoft Access first looks for the report with this name in the library database, and then in the current database.</p></td>
</tr>
<tr class="even">
<td><p>View</p></td>
<td><p>The view in which the report will open. Click <strong>Print</strong> (print the report immediately), <strong>Design</strong>, or <strong>Print Preview</strong> in the <strong>View</strong> box. The default is <strong>Print</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>Filter Name</p></td>
<td><p>A filter that restricts the report's records. You can enter the name of either an existing query or a filter that was saved as a query. However, the query must include all the fields in the report you are opening or have its <strong>OutputAllFields</strong> property set to <strong>Yes</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Where Condition</p></td>
<td><p>A valid SQL WHERE clause (without the word WHERE) or expression that Access uses to select records from the report's underlying table or query. If you select a filter with the Filter Name argument, Access applies this WHERE clause to the results of the filter. To open a report and restrict its records to those specified by the value of a control on a form, use the following expression:<br />
<strong>[</strong><em>fieldname</em><strong>] = Forms![</strong><em>formname</em><strong>]![</strong><em>controlname on form</em><strong>]</strong><br />
Replace <em>fieldname</em> with the name of a field in the underlying table or query of the report you want to open. Replace <em>formname</em> and <em>controlname on form</em> with the name of the form and the control on the form that contains the value you want records in the report to match.</p>

> [!NOTE]
> <P>The maximum length of the Where Condition argument is 255 characters. If you need to enter a more complex SQL WHERE clause longer than this, use the <STRONG>OpenReport</STRONG> method of the <STRONG>DoCmd</STRONG> object in a Visual Basic for Applications (VBA) module instead. You can enter SQL WHERE clause statements of up to 32,768 characters in VBA.</P>


<p></p></td>
</tr>
<tr class="odd">
<td><p>Window Mode</p></td>
<td><p>The mode in which the report will open. Click <strong>Normal</strong>, <strong>Hidden</strong>, <strong>Icon</strong>, or <strong>Dialog</strong> in the <strong>Window Mode</strong> box. The default is <strong>Normal</strong>.</p>

> [!NOTE]
> <P>Some Window Mode argument settings do not apply when using tabbed documents. To switch to overlapping windows:</P>


<p></p>
<ol>
<li><p>and then click <strong>Options</strong>.</p></li>
<li><p>In the <strong>Access Options</strong> dialog box, click <strong>Current Database</strong>.</p></li>
<li><p>In the <strong>Application Options</strong> section, under <strong>Document Window Options</strong>, click <strong>Overlapping Windows</strong>.</p></li>
<li><p>Click <strong>OK</strong>, then close and reopen the database.</p></li>
</ol></td>
</tr>
</tbody>
</table>


## Remarks

The **Print** setting for the **View** argument prints the report immediately by using the current printer settings, without bringing up the **Print** dialog box. You can also use the **OpenReport** action to open and set up a report and then use the PrintOut action to print it. For example, you may want to modify the report or use the **PrintOut** action to change the printer settings before you print.

The filter and WHERE condition you apply become the setting of the report's **Filter** property.

The **OpenReport** action is similar to double-clicking the report in the Navigation Pane, or right-clicking the report in the Navigation Pane and selecting a view or the **Print** command.

**Tips**

  - To print similar reports for different sets of data, use a filter or a WHERE clause to restrict the records printed in the report. Then edit the macro to apply a different filter or change the Where Condition argument.

  - You can drag a report from the Navigation Pane to a macro action row. This automatically creates an **OpenReport** action that opens the report in Report view.

## Example

The following example shows how to use the OpenReport action to pass a parameter that filters a report as it is opened. The **rptChapters** report displays the records for the specified author by passing the item selected in the **cboAuthors** combo box to the SelectedAuthor parameter.

**Sample code provided by:** The [Microsoft Access 2010 Programmer’s Reference](http://www.wrox.com/wileycda/wroxtitle/access-2010-programmer-s-reference.productcd-0470591668.html)

    OpenReport
        Report Name rptChapters
        View Report
        Filter Name
        Where Condition
        Window Mode Normal
    
    Parameters
        SelectedAuthor =[cboAuthor]

## About the Contributors

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems.

