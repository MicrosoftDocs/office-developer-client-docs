---
title: MarshalOptionsEnum (Access desktop database reference)
TOCTitle: MarshalOptionsEnum
ms:assetid: 5361884b-a0fe-c480-1b9f-18e53be77f86
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249272(v=office.15)
ms:contentKeyID: 48544867
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MarshalOptionsEnum


**Applies to**: Access 2013 | Office 2013

Specifies which records should be returned to the server.

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
<td><p><strong>adMarshalAll</strong></p></td>
<td><p>0</p></td>
<td><p>Default. Returns all rows to the server.</p></td>
</tr>
<tr class="even">
<td><p><strong>adMarshalModifiedOnly</strong></p></td>
<td><p>1</p></td>
<td><p>Returns only modified rows to the server.</p></td>
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
<td><p>AdoEnums.MarshalOptions.ALL</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.MarshalOptions.MODIFIEDONLY</p></td>
</tr>
</tbody>
</table>

