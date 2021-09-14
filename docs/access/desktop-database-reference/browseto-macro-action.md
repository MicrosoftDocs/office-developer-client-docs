---
title: BrowseTo macro action
TOCTitle: BrowseTo macro action
ms:assetid: b25e1cc6-c4ed-abd6-0285-94fc7dae0bdf
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822020(v=office.15)
ms:contentKeyID: 48547167
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm35083
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# BrowseTo macro action

**Applies to**: Access 2013, Office 2013

You can use the **BrowseTo** action to navigate between objects in place. You can also change the source object of a subform control by specifying the Path to Subform Control argument. Use **BrowseTo** to navigate from form1 to form2 without opening up a new window.

## Setting

The **BrowseTo** action has the following argument.

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
<td><p>Object Type</p></td>
<td><p>The object type to which to browse.</p></td>
</tr>
<tr class="even">
<td><p>Object Name</p></td>
<td><p>The object that loads inside the subform control referenced by the Path to Subform Control argument.</p></td>
</tr>
<tr class="odd">
<td><p>Path to Subform Control</p></td>
<td><p>If specified, the path from the main form of the application to the target subform control that loads the object specified by the Object Name argument.</p></td>
</tr>
<tr class="even">
<td><p>Where Condition</p></td>
<td><p>If specified, replaces the Where condition of the object record source.</p></td>
</tr>
<tr class="odd">
<td><p>Page</p></td>
<td><p>If specified, sets the page of the continuous form that will be made the current page. This argument is web only.</p></td>
</tr>
<tr class="even">
<td><p>Data Mode</p></td>
<td><p>If specified, the data entry mode of the form.</p></td>
</tr>
</tbody>
</table>


## Remarks

The PathToSubFormControl argument must be specified using the syntax in the following code example:

```vb
    Main Form.SubForm Ctrl 1>Form 2.SubForm Ctrl 2>Form 3.SubFormCtrl3
```

In this example, the Main Form is the top level form in the Access client application. The Path to Sub Form Control argument must alternately specify form and subform control names leading from the main form to the subform control that is the container of the object specified by the Object Name argument. Each subform control specified must be a control on the form that precedes it. The path must end with a subform control.

## Example

The following example shows how to use the BrowseTo action to open a report in a subform control or within a navigation control.

**Sample code provided by** the [Microsoft Access 2010 Programmer’s Reference](https://www.amazon.com/Microsoft-Access-2010-Programmers-Reference/dp/8126528125).

```vb
    OnError
        Go to Next
        Macro Name
    
    /* Try to load the report in the host form (frmAuthorsParameter)    */
    BrowseTo
        Object Type Report
        Object Name rptChapters
        Path to Subform Control frmAuthorsParameter.sfrmChild
        Where Condition
        Page
        Data Mode Edit
    
    Parameters
        SelectedAuthor =[cboAuthor]
    
    /* if this fails, try to load it in the navigation subform     */
    BrowseTo
        Object Type Report
        Object Name rptChapters
        Path to Subform Control frmMain.NavigationSubform>frmAuthorsParameter.sfrmChild
        Where Condition
        Page
        Data Mode Edit
    
    Parameters
        SelectedAuthor =[cboAuthor]
```



