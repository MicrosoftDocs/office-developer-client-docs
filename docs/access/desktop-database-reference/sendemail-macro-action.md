---
title: SendEmail macro action
TOCTitle: SendEmail macro action
ms:assetid: 84ff6b46-d239-4716-9964-5b909656d347
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196780(v=office.15)
ms:contentKeyID: 48546046
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# SendEmail macro action

**Applies to**: Access 2013, Office 2013

The **SendEmail** action sends an email message.

> [!NOTE]
> The **SendEmail** action is available only in Data Macros.

## Setting

The **SendEmail** action has the following arguments.

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
<td><p><strong>To</strong></p></td>
<td><p>Yes</p></td>
<td><p>The recipients of the message whose names you want to put on the <strong>To</strong> line in the message.Separate the recipient names that you specify in this argument (and in the <em>Cc</em> and <em>Bcc</em> arguments) with a semicolon (;).</p></td>
</tr>
<tr class="even">
<td><p><strong>Cc</strong></p></td>
<td><p>No</p></td>
<td><p>The message recipients whose names you want to put on the Cc (&quot;carbon copy&quot;) line in the message.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Bcc</strong></p></td>
<td><p>No</p></td>
<td><p>The message recipients whose names you want to put on the Bcc (&quot;blind carbon copy&quot;) line in the message.</p></td>
</tr>
<tr class="even">
<td><p><strong>Subject</strong></p></td>
<td><p>No</p></td>
<td><p>The subject of the message. This text appears on the <strong>Subject</strong> line in the message.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Body</strong></p></td>
<td><p>No</p></td>
<td><p>The text that you want to include in the main body of the mail message. If you leave this argument blank, no additional text is included in the message.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **SendEmail** action is available only in the **[After Delete](after-delete-macro-event.md)**, **[After Insert](after-insert-macro-event.md)**, and **[After Update](after-update-macro-event.md)** macro events.

The **SendEmail** action does not display the message for editing.

