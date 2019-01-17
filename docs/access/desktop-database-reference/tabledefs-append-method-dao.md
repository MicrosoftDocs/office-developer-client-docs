---
title: TableDefs.Append method (DAO)
TOCTitle: Append Method
ms:assetid: f951a3c4-dade-c1ef-3bfc-6b2a60e12adc
ms:mtpsurl: https://msdn.microsoft.com/library/Ff837001(v=office.15)
ms:contentKeyID: 48548811
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# TableDefs.Append method (DAO)

**Applies to**: Access 2013, Office 2013

Adds a new **TableDef** to the **TableDefs** collection.

## Syntax

*expression* .Append(***Object***)

*expression* A variable that represents a **TableDefs** object.

## Parameters

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Required/optional</p></th>
<th><p>Data type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Object</em></p></td>
<td><p>Required</p></td>
<td><p><strong>Object</strong></p></td>
<td><p>An object variable that represents the field being appended to the collection.</p></td>
</tr>
</tbody>
</table>


## Remarks

The appended object becomes a persistent object, stored on disk, until you delete it by using the **Delete** method.

The addition of a new object occurs immediately, but you should use the **Refresh** method on any other collections that may be affected by changes to the database structure.

If the object you're appending isn't complete (such as when you haven't appended any **Field** objects to a **Fields** collection of an **Index** object before it's appended to an **Indexes** collection) or if the properties set in one or more subordinate objects are incorrect, using the **Append** method causes an error. For example, if you haven’t specified a field type and then try to append the **Field** object to the **Fields** collection in a **TableDef** object, using the **Append** method triggers a run-time error.

