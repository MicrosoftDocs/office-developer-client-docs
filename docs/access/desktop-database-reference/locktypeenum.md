---
title: LockTypeEnum (Access desktop database reference)
TOCTitle: LockTypeEnum
ms:assetid: 966b4952-5591-4a99-82d5-99cb9ae3fc72
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249667(v=office.15)
ms:contentKeyID: 48546448
ms.date: 09/18/2015
mtps_version: v=office.15
---

# LockTypeEnum


**Applies to**: Access 2013 | Office 2013

Specifies the type of lock placed on records during editing.

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
<td><p><strong>adLockBatchOptimistic</strong></p></td>
<td><p>4</p></td>
<td><p>Indicates optimistic batch updates. Required for batch update mode.</p></td>
</tr>
<tr class="even">
<td><p><strong>adLockOptimistic</strong></p></td>
<td><p>3</p></td>
<td><p>Indicates optimistic locking, record by record. The provider uses optimistic locking, locking records only when you call the <a href="update-method-ado.md">Update</a> method.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adLockPessimistic</strong></p></td>
<td><p>2</p></td>
<td><p>Indicates pessimistic locking, record by record. The provider does what is necessary to ensure successful editing of the records, usually by locking records at the data source immediately after editing.</p></td>
</tr>
<tr class="even">
<td><p><strong>adLockReadOnly</strong></p></td>
<td><p>1</p></td>
<td><p>Indicates read-only records. You cannot alter the data.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adLockUnspecified</strong></p></td>
<td><p>-1</p></td>
<td><p>Does not specify a type of lock. For clones, the clone is created with the same lock type as the original.</p></td>
</tr>
</tbody>
</table>


### ADO/WFC equivalent

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
<td><p>AdoEnums.LockType.BATCHOPTIMISTIC</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.LockType.OPTIMISTIC</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.LockType.PESSIMISTIC</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.LockType.READONLY</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.LockType.UNSPECIFIED</p></td>
</tr>
</tbody>
</table>

