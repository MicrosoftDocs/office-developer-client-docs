---
title: Cursor and Lock Characteristics
TOCTitle: Cursor and Lock Characteristics
ms:assetid: 5f8b6700-14f6-d342-42f6-cc8e89c71a1a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249347(v=office.15)
ms:contentKeyID: 48545164
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Cursor and Lock Characteristics


_**Applies to:** Access 2013 | Office 2013_

While the characteristics of a cursor depend upon capabilities of the provider, the following advantages and disadvantages generally apply to the various types of cursors and locks.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Cursor or lock type</p></th>
<th><p>Advantages</p></th>
<th><p>Disadvantages</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>adOpenForwardOnly</strong></p></td>
<td><p></p>
<ul>
<li><p>Low resource requirements</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>Cannot scroll backward</p></li>
<li><p>No data concurrency</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>adOpenStatic</strong></p></td>
<td><p></p>
<ul>
<li><p>Scrollable</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>No data concurrency</p></li>
</ul>
<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>adOpenKeyset</strong></p></td>
<td><p></p>
<ul>
<li><p>Some data concurrency</p></li>
<li><p>Scrollable</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>Higher resource requirements</p></li>
<li><p>Not available in disconnected scenario</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>adOpenDynamic</strong></p></td>
<td><p></p>
<ul>
<li><p>High data concurrency</p></li>
<li><p>Scrollable</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>Highest resource requirements</p></li>
<li><p>Not available in disconnected scenario</p></li>
</ul>
<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>adLockReadOnly</strong></p></td>
<td><p></p>
<ul>
<li><p>Low resource requirements</p></li>
<li><p>Highly scalable</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>Data not updatable through cursor</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>adLockBatchOptimistic</strong></p></td>
<td><p></p>
<ul>
<li><p>Batch updates</p></li>
<li><p>Allows disconnected scenarios</p></li>
<li><p>Other users able to access data</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>Data can be changed by multiple users at once</p></li>
</ul>
<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>adLockPessimistic</strong></p></td>
<td><p></p>
<ul>
<li><p>Data cannot be changed by other users while locked</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>Prevents other users from accessing data while locked</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>adLockOptimistic</strong></p></td>
<td><p></p>
<ul>
<li><p>Other users able to access data</p></li>
</ul>
<p></p></td>
<td><p></p>
<ul>
<li><p>Data can be changed by multiple users at once</p></li>
</ul>
<p></p></td>
</tr>
</tbody>
</table>

