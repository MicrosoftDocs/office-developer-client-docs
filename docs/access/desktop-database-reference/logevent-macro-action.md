---
title: LogEvent macro action
TOCTitle: LogEvent macro action
ms:assetid: 3578c725-64b9-385e-ef73-a15cdf751c33
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192460(v=office.15)
ms:contentKeyID: 48544148
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# LogEvent macro action

**Applies to**: Access 2013, Office 2013

The **LogEvent** action writes information to the **USysApplicationLog** system table.

> [!NOTE]
> The **LogEvent** action is available only in Data Macros.

## Setting

The **LogEvent** action has the following arguments.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Description</strong></p></td>
<td><p>No</p></td>
<td><p>A string expression that describes the condition that you want to log. The description cannot exceed 255 characters.</p></td>
</tr>
</tbody>
</table>

## Remarks

The **LogEvent** action can be used to write status information to the **USysApplicationLog** system table that does not merit using the **[RaiseError](raiseerror-macro-action.md)** action to throw an error. For example, you could log changes to a specific field, or use the items written to the **USysApplicationLog** to assist you in debugging your macro.

When you use the **LogEvent** action to write to the **USysApplicationLog** table, the **Category** column is automatically set to **User**.

To see the **USysApplicationLog** table, use the following steps:

1.  Click the **File** menu,and then click **Options**.

2.  In the **Access Options** dialog box, click the **Current Database** tab.

3.  In the **Navigation** section, click **Navigation Options**.

4.  In the **Navigation Options** dialog box, click **Show System Objects**, and then click **OK**.

5.  Click **OK** to dismiss the **Access Options** dialog box.

