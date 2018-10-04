---
title: PositionEnum
TOCTitle: PositionEnum
ms:assetid: 2a6f294b-74f2-b951-e32a-79ff5e782204
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249054(v=office.15)
ms:contentKeyID: 48543907
ms.date: 09/18/2015
mtps_version: v=office.15
---

# PositionEnum


_**Applies to:** Access 2013 | Office 2013_

Specifies the current position of the record pointer within a [Recordset](recordset-object-ado.md).

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
<td><p><strong>adPosBOF</strong></p></td>
<td><p>-2</p></td>
<td><p>Indicates that the current record pointer is at BOF (that is, the <a href="bof-eof-properties-ado.md">BOF</a> property is <strong>True</strong>).</p></td>
</tr>
<tr class="even">
<td><p><strong>adPosEOF</strong></p></td>
<td><p>-3</p></td>
<td><p>Indicates that the current record pointer is at EOF (that is, the <a href="bof-eof-properties-ado.md">EOF</a> property is <strong>True</strong>).</p></td>
</tr>
<tr class="odd">
<td><p><strong>adPosUnknown</strong></p></td>
<td><p>-1</p></td>
<td><p>Indicates that the <strong>Recordset</strong> is empty, the current position is unknown, or the provider does not support the <a href="absolutepage-property-ado.md">AbsolutePage</a> or <a href="absoluteposition-property-ado.md">AbsolutePosition</a> property.</p></td>
</tr>
</tbody>
</table>


**ADO/WFC Equivalent**

Package: **com.ms.wfc.data**

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AdoEnums.Position.BOF</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Position.EOF</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Position.UNKNOWN</p></td>
</tr>
</tbody>
</table>

