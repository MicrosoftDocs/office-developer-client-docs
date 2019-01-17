---
title: ADO MD objects (Access desktop database reference)
TOCTitle: ADO MD objects
ms:assetid: 13501e44-70b6-1036-a8b7-c276f187e4f4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248907(v=office.15)
ms:contentKeyID: 48543366
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# ADO MD objects

**Applies to**: Access 2013, Office 2013

<br/>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="even">
<th>Object</th>
<th>Description</th>
</tr>
<tr class="odd">
<td><p><a href="axis-object-ado-md.md">Axis</a></p></td>
<td><p>Represents a positional or filter axis of a cellset, containing selected members of one or more dimensions.</p></td>
</tr>
<tr class="even">
<td><p><a href="catalog-object-ado-md.md">Catalog</a></p></td>
<td><p>Contains multidimensional schema information (that is, cubes and underlying dimensions, hierarchies, levels, and members) specific to a multidimensional data provider (MDP).</p></td>
</tr>
<tr class="odd">
<td><p><a href="cell-object-ado-md.md">Cell</a></p></td>
<td><p>Represents the data at the intersection of axis coordinates, contained in a cellset.</p></td>
</tr>
<tr class="even">
<td><p><a href="cellset-object-ado-md.md">Cellset</a></p></td>
<td><p>Represents the results of a multidimensional query. It is a collection of cells selected from cubes or other cellsets.</p></td>
</tr>
<tr class="odd">
<td><p><a href="cubedef-object-ado-md.md">CubeDef</a></p></td>
<td><p>Represents a cube from a multidimensional schema, containing a set of related dimensions.</p></td>
</tr>
<tr class="even">
<td><p><a href="dimension-object-ado-md.md">Dimension</a></p></td>
<td><p>Represents one of the dimensions of a multidimensional cube, containing one or more hierarchies of members.</p></td>
</tr>
<tr class="odd">
<td><p><a href="hierarchy-object-ado-md.md">Hierarchy</a></p></td>
<td><p>Represents one way in which the members of a dimension can be aggregated or &quot;rolled up.&quot; A dimension can be aggregated along one or more hierarchies.</p></td>
</tr>
<tr class="even">
<td><p><a href="level-object-ado-md.md">Level</a></p></td>
<td><p>Contains a set of members, each of which has the same rank within a hierarchy.</p></td>
</tr>
<tr class="odd">
<td><p><a href="member-object-ado-md.md">Member</a></p></td>
<td><p>Represents a member of a level in a cube, the children of a member of a level, or a member of a position along an axis of a cellset.</p></td>
</tr>
<tr class="even">
<td><p><a href="position-object-ado-md.md">Position</a></p></td>
<td><p>Represents a set of one or more members of different dimensions that defines a point along an axis.</p></td>
</tr>
</tbody>
</table>

<br/>

Also, the **Catalog** object is connected to an ADO **Connection** object, which is included with the standard ADO library:

<br/>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Object</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="connection-object-ado.md">Connection</a></p></td>
<td><p>Represents an open connection to a data source.</p></td>
</tr>
</tbody>
</table>

<br/>

Many ADO MD objects can be contained in a corresponding collection. For example, a [CubeDef](cubedef-object-ado-md.md) object can be contained in a [CubeDefs](cubedefs-collection-ado-md.md) collection of a **Catalog**. For more information, see [ADO MD Collections](ado-md-collections.md).

