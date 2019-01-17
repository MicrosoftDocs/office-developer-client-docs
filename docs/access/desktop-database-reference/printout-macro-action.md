---
title: PrintOut macro action
TOCTitle: PrintOut macro action
ms:assetid: 13688158-1cf1-4b2e-d90a-271c8890e413
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845432(v=office.15)
ms:contentKeyID: 48543368
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm1697
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# PrintOut macro action

**Applies to**: Access 2013, Office 2013

You can use the **PrintOut** action to print the active object in the open database. You can print datasheets, reports, forms, data access pages, and modules.

> [!NOTE]
> This action will not be allowed if the database is not trusted. 

## Setting

The **PrintOut** action has the following arguments.

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
<td><p><strong>Print Range</strong></p></td>
<td><p>The range to print. Click <strong>All</strong> (the user can print all of the object), <strong>Selection</strong> (the user can print the part of the object that's selected), or <strong>Pages</strong> (the user can specify a range of pages in the <strong>Page From</strong> and <strong>Page To</strong> arguments) in the <strong>Print Range</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. The default is <strong>All</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Page From</strong></p></td>
<td><p>The first page to print. Printing starts at the top of this page. This argument is required if you select <strong>Pages</strong> in the <strong>Print Range</strong> box.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Page To</strong></p></td>
<td><p>The last page to print. Printing stops at the bottom of this page. This argument is required if you select <strong>Pages</strong> in the <strong>Print Range</strong> box.</p></td>
</tr>
<tr class="even">
<td><p><strong>Print Quality</strong></p></td>
<td><p>The print quality. Click <strong>High</strong>, <strong>Medium</strong>, <strong>Low</strong>, or <strong>Draft</strong>. The lower the quality, the faster the object prints. The default is <strong>High</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Copies</strong></p></td>
<td><p>The number of copies to print. The default is 1.</p></td>
</tr>
<tr class="even">
<td><p><strong>Collate Copies</strong></p></td>
<td><p>Click <strong>Yes</strong> (collate the printed copies) or <strong>No</strong> (do not collate copies). The object may print faster if this argument is set to <strong>No</strong>. The default is <strong>Yes</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

This action is similar to selecting an object, clicking the **File** tab and then clicking **Print**. With this action, however, no **Print** dialog box appears.

> [!TIP]
> If you have particular print settings you use frequently, create a macro containing a **PrintOut** action with these settings in its arguments.

The arguments for this action correspond to options in the **Print** dialog box. However, unlike the **FindRecord** action and **Find and Replace** dialog box, the argument settings aren't shared with the **Print** dialog box options.

To run the **PrintOut** action in a Visual Basic for Applications (VBA) module, use the **PrintOut** method of the **DoCmd** object.

