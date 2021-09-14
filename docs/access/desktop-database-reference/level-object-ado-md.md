---
title: Level object (ADO MD)
TOCTitle: Level object (ADO MD)
ms:assetid: ddbcabce-8777-1068-98a3-be209084f497
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250121(v=office.15)
ms:contentKeyID: 48548160
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Level object (ADO MD)


**Applies to**: Access 2013, Office 2013

Contains a set of members, each of which has the same rank within a hierarchy.

## Remarks

With the collections and properties of a **Level** object, you can do the following:

  - Identify the **Level** with the [Name](name-property-ado-md.md) and [UniqueName](uniquename-property-ado-md.md) properties.

  - Return a string to use when displaying the **Level** with the [Caption](caption-property-ado-md.md) property.

  - Return a meaningful string that describes the **Level** with the [Description](description-property-ado-md.md) property.

  - Return the [Member](member-object-ado-md.md) objects that make up the **Level** with the [Members](members-collection-ado-md.md) collection.

  - Return the number of levels from the root of the **Level** with the [Depth](depth-property-ado-md.md) property.

  - Use the standard ADO [Properties](properties-collection-ado.md) collection to obtain additional information about the **Level** object.

The **Properties** collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CatalogName</p></td>
<td><p>The name of the catalog to which this cube belongs.</p></td>
</tr>
<tr class="even">
<td><p>CubeName</p></td>
<td><p>The name of the cube.</p></td>
</tr>
<tr class="odd">
<td><p>Description</p></td>
<td><p>A meaningful description of the level.</p></td>
</tr>
<tr class="even">
<td><p>DimensionUniqueName</p></td>
<td><p>The unambiguous name of the <a href="dimension-object-ado-md.md">dimension</a>.</p></td>
</tr>
<tr class="odd">
<td><p>HierarchyUniqueName</p></td>
<td><p>The unambiguous name of the hierarchy.</p></td>
</tr>
<tr class="even">
<td><p>LevelCaption</p></td>
<td><p>A label or caption associated with the level.</p></td>
</tr>
<tr class="odd">
<td><p>LevelCardinality</p></td>
<td><p>The number of members in the level.</p></td>
</tr>
<tr class="even">
<td><p>LevelGUID</p></td>
<td><p>The GUID of the level.</p></td>
</tr>
<tr class="odd">
<td><p>LevelName</p></td>
<td><p>Name of the level.</p></td>
</tr>
<tr class="even">
<td><p>LevelNumber</p></td>
<td><p>The distance between the level and the root of the hierarchy.</p></td>
</tr>
<tr class="odd">
<td><p>LevelType</p></td>
<td><p>The type of level.</p></td>
</tr>
<tr class="even">
<td><p>LevelUniqueName</p></td>
<td><p>The unambiguous name of the level.</p></td>
</tr>
<tr class="odd">
<td><p>SchemaName</p></td>
<td><p>The name of the schema to which this cube belongs.</p></td>
</tr>
</tbody>
</table>

