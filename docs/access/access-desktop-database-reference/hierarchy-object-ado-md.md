---
title: Hierarchy Object (ADO MD)
TOCTitle: Hierarchy Object (ADO MD)
ms:assetid: 26e4e690-59ad-fb87-66b0-f3310df42d0c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249031(v=office.15)
ms:contentKeyID: 48543825
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Hierarchy Object (ADO MD)


_**Applies to:** Access 2013 | Office 2013_

Represents one way in which the members of a [dimension](dimension-object-ado-md.md) can be aggregated or "rolled up." A dimension can be aggregated along one or more hierarchies.

## Remarks

With the collections and properties of a **Hierarchy** object, you can do the following:

  - Identify the **Hierarchy** with the [Name](name-property-ado-md.md) and [UniqueName](uniquename-property-ado-md.md) properties.

  - Return a meaningful string that describes the **Hierarchy** with the [Description](description-property-ado-md.md) property.

  - Return the [Level](level-object-ado-md.md) objects that make up the **Hierarchy** with the [Levels](levels-collection-ado-md.md) collection.

  - Use the standard ADO [Properties](properties-collection-ado.md) collection to obtain additional information about the **Hierarchy** object.

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
<td><p>AllMember</p></td>
<td><p>The member at the highest level of rollup in the hierarchy.</p></td>
</tr>
<tr class="even">
<td><p>CatalogName</p></td>
<td><p>The name of the catalog to which this cube belongs.</p></td>
</tr>
<tr class="odd">
<td><p>CubeName</p></td>
<td><p>The name of the cube.</p></td>
</tr>
<tr class="even">
<td><p>DefaultMember</p></td>
<td><p>The unique name of the default member for this hierarchy.</p></td>
</tr>
<tr class="odd">
<td><p>Description</p></td>
<td><p>A meaningful description of the hierarchy.</p></td>
</tr>
<tr class="even">
<td><p>DimensionType</p></td>
<td><p>The type of dimension to which this hierarchy belongs.</p></td>
</tr>
<tr class="odd">
<td><p>DimensionUniqueName</p></td>
<td><p>The unambiguous name of the dimension.</p></td>
</tr>
<tr class="even">
<td><p>HierarchyCaption</p></td>
<td><p>A label or caption associated with the hierarchy.</p></td>
</tr>
<tr class="odd">
<td><p>HierarchyCardinality</p></td>
<td><p>The number of members in the hierarchy.</p></td>
</tr>
<tr class="even">
<td><p>HierarchyGUID</p></td>
<td><p>The GUID of the hierarchy.</p></td>
</tr>
<tr class="odd">
<td><p>HierarchyName</p></td>
<td><p>The name of the hierarchy.</p></td>
</tr>
<tr class="even">
<td><p>HierarchyUniqueName</p></td>
<td><p>The unambiguous name of the hierarchy.</p></td>
</tr>
<tr class="odd">
<td><p>SchemaName</p></td>
<td><p>The name of the schema to which this cube belongs.</p></td>
</tr>
</tbody>
</table>

