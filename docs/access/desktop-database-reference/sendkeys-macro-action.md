---
title: SendKeys macro action
TOCTitle: SendKeys macro action
ms:assetid: 3b06fcfc-ea64-c780-b5fc-6fc72853f524
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192656(v=office.15)
ms:contentKeyID: 48544275
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm183441
f1_categories:
- Office.Version=v15
---

# SendKeys macro action

**Applies to**: Access 2013, Office 2013

<table>
<thead>
<tr class="header">
<th><img src="media/access-alert-security.gif" title="Security note" alt="Security note" /><strong>Security Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Avoid using the <strong>SendKeys</strong> statement or an AutoKeys macro with sensitive or confidential information. A malicious user could intercept the keystrokes and compromise the security of your computer and data.</td>
</tr>
</tbody>
</table>

You can use the **SendKeys** action to send keystrokes directly to Microsoft Access or to an active Windows-based application.

> [!NOTE]
> This action will not be allowed if the database is not trusted. 

## Setting

The **SendKeys** action has the following arguments.

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
<td><p><strong>Keystrokes</strong></p></td>
<td><p>The keystrokes you want Access or the application to process. Enter the keystrokes in the <strong>Keystrokes</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. You can type up to 255 characters. This is a required argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>Wait</strong></p></td>
<td><p>Specifies whether the macro should pause until the keystrokes have been processed. Click <strong>Yes</strong> (to pause) or <strong>No</strong> (to not pause). The default is <strong>No</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

Access processes the keystrokes it receives through the **SendKeys** action exactly as if you had typed them directly in an Access window.

To specify the keystrokes, use the same syntax as you would for the **SendKeys** statement.

> [!NOTE]
> An error can occur if the **Keystrokes** argument contains incorrect syntax, misspelled text, or other values that aren't appropriate for the window the keystrokes are sent to.

You can use this action to enter information in a dialog box, particularly if you don't want to interrupt the macro to respond manually to the dialog box. Some Access actions, such as **PrintOut** and **FindRecord**, automatically select the options in certain frequently used dialog boxes. You can use the **SendKeys** action to select the options in less commonly used dialog boxes.

> [!NOTE]
> - Because the dialog box suspends the macro, you must put the **SendKeys** action before the action that causes the dialog box to open and set the **Wait** argument to **No**.
> - The timing of the keystrokes reaching Access or another application can be tricky. As a result, it's recommended that if there's some other method (such as the **FindRecord** action) you can use to achieve a desired task, use that method rather than using the **SendKeys** action to fill in the options in a dialog box.

If you want to send more than 255 characters to Access or another Windows-based application, you can use several **SendKeys** actions in succession in a macro.

Using the **SendKeys** action to send keystrokes triggers the appropriate **KeyDown**, **KeyUp**, and **KeyPress** events. Sending non-ANSI keystrokes (such as a function key) doesn't trigger the **KeyPress** event.

This action isn't available from a Visual Basic for Applications (VBA) module. Use the **SendKeys** statement instead.

