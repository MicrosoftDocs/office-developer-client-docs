---
title: SelectObject macro action
TOCTitle: SelectObject macro action
ms:assetid: a90539a0-c5a0-e997-9c25-e0972d28f2a6
ms:mtpsurl: https://msdn.microsoft.com/library/Ff821420(v=office.15)
ms:contentKeyID: 48546914
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm41840
f1_categories:
- Office.Version=v15
---

# SelectObject macro action

**Applies to**: Access 2013, Office 2013

You can use the **SelectObject** action to select a specified database object.

## Setting

The **SelectObject** action has the following arguments.

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
<td><p>The type of database object to select. Click <strong>Table</strong>, <strong>Query</strong>, <strong>Form</strong>, <strong>Report</strong>, <strong>Macro</strong>, <strong>Module</strong>, <strong>Data Access Page</strong>, <strong>Server View</strong>, <strong>Diagram</strong>, <strong>Stored Procedure</strong>, or <strong>Function</strong> in the <strong>Object Type</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. This is a required argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>Object Name</strong></p></td>
<td><p>The name of the object to select. The <strong>Object Name</strong> box shows all objects in the database of the type selected by the <strong>Object Type</strong> argument. This is a required argument, unless you set the In Navigation Pane argument to <strong>Yes</strong>.</p><p><strong>NOTE</strong>: The object names for <STRONG>Server View</STRONG>, <STRONG>Diagram</STRONG>, or <STRONG>Stored Procedure</STRONG> objects are not displayed in the <STRONG>Object Name</STRONG> box of an Access project (.adp).</p></td>
</tr>
<tr class="odd">
<td><p><strong>In Navigation Pane</strong></p></td>
<td><p>Specifies whether Microsoft Access selects the object in the Navigation Pane. Click <strong>Yes</strong> (to select the object in the Navigation Pane) or <strong>No</strong> (not to select the object in the Navigation Pane). The default is <strong>No</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **SelectObject** action works with any Access object that can receive the focus. This action gives the specified object the focus and shows the object if it's hidden. If the object is a form, the **SelectObject** action sets the form's **Visible** property to **Yes** and returns the form to the mode set by its form properties (for example, as a modal or pop-up form).

If the object isn't open in one of the other Access windows, you can select it in the Navigation Pane by setting the **In Navigation Pane** argument to **Yes**. If you set the **In Navigation Pane** argument to **No**, an error message appears when you try to select an object that isn't open.

Often, you might use this action to select an object on which you want to perform additional actions. For example, if you have Access configured to use overlapping windows instead of tabbed documents, you may want to restore an object that has been minimized (by using the **RestoreWindow** action) or maximize a window that contains an object you want to work with (by using the **MaximizeWindow** action).

If you select a form, you can use the **GoToControl**, **GoToRecord**, and **GoToPage** actions to move to specific areas on the form. The **GoToRecord** action also works for datasheets.

To run the **SelectObject** action in a Visual Basic for Applications (VBA) module, use the **SelectObject** method of the **DoCmd** object.

