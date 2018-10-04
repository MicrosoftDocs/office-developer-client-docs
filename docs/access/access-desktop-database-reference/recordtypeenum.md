---
title: RecordTypeEnum
TOCTitle: RecordTypeEnum
ms:assetid: 7edd6508-1507-4649-f1aa-03f1873ef09c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249534(v=office.15)
ms:contentKeyID: 48545890
ms.date: 09/18/2015
mtps_version: v=office.15
---

# RecordTypeEnum


_**Applies to:** Access 2013 | Office 2013_

Specifies the type of [Record](record-object-ado.md) object.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>adSimpleRecord</strong></p></td>
<td><p>0</p></td>
<td><p>Indicates a <em>simple</em> record (does not contain child nodes).</p></td>
</tr>
<tr class="even">
<td><p><strong>adCollectionRecord</strong></p></td>
<td><p>1</p></td>
<td><p>Indicates a <em>collection</em> record (contains child nodes).</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRecordUnknown</strong></p></td>
<td><p>-1</p></td>
<td><p>Indicates that the type of this <strong>Record</strong> is unknown.</p></td>
</tr>
<tr class="even">
<td><p><strong>adStructDoc</strong></p></td>
<td><p>2</p></td>
<td><p>Indicates a special kind of <em>collection</em> record that represents COM structured documents.</p></td>
</tr>
</tbody>
</table>


**ADO/WFC Equivalent**

These constants do not have ADO/WFC equivalents.

