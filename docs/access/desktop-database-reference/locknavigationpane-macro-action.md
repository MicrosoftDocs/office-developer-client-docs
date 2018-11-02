---
title: LockNavigationPane macro action
TOCTitle: LockNavigationPane macro action
ms:assetid: abf7a989-c7cf-3efa-8df4-3c5b075d0e5f
ms:mtpsurl: https://msdn.microsoft.com/library/Ff821487(v=office.15)
ms:contentKeyID: 48546986
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm172454
f1_categories:
- Office.Version=v15
---

# LockNavigationPane macro action


**Applies to**: Access 2013, Office 2013

You can use the **LockNavigationPane** action to prevent users from deleting database objects that are displayed in the Navigation Pane.

## Setting

The **LockNavigationPane** action has the following argument.

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
<td><p><strong>Lock</strong></p></td>
<td><p>Select <strong>Yes</strong> to lock the Navigation Pane, or <strong>No</strong> to unlock the Navigation Pane.</p></td>
</tr>
</tbody>
</table>


## Remarks

Locking the Navigation Pane prevents you from deleting database objects or cutting database objects to the clipboard. It does *not* prevent you from performing any of the following operations:

  - Copying database objects to the clipboard

  - Pasting database objects from the clipboard

  - Displaying or hiding the Navigation Pane

  - Selecting different Navigation Pane organization schemes

  - Showing or hiding sections of the Navigation Pane

To run the **LockNavigationPane** action in a VBA module, use the **LockNavigationPane** method of the **DoCmd** object.

