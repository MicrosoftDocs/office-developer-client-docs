---
title: Customization File Logs section
TOCTitle: Customization File Logs section
ms:assetid: de331a97-c9cd-5f02-692b-d7afd9e9342a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250124(v=office.15)
ms:contentKeyID: 48548178
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Customization File Logs section

**Applies to**: Access 2013, Office 2013

The **logs** section contains a log file entry, which specifies the name of a file that records errors during the operation of the **DataFactory**.

## Syntax

A log file entry is of the form:

`err=FileName`

<br/>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>err</strong></p></td>
<td><p>A literal string that indicates this is a log file entry.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>A complete path and file name. The typical file name is <strong>c:\msdfmap.log</strong>.</p></td>
</tr>
</tbody>
</table>


The log file will contain the user name, HRESULT, date, and time of each error.

