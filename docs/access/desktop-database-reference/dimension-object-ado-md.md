---
title: Dimension object (ADO MD)
TOCTitle: Dimension object (ADO MD)
ms:assetid: 12f43cfc-c74e-a2e8-7f6e-75fc68472c4b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248902(v=office.15)
ms:contentKeyID: 48543355
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Dimension object (ADO MD)


**Applies to**: Access 2013, Office 2013

Represents one of the dimensions of a multidimensional cube, containing one or more hierarchies of members.

## Remarks

With the collections and properties of a **Dimension** object, you can do the following:

  - Identify the **Dimension** with the [Name](name-property-ado-md.md) and [UniqueName](uniquename-property-ado-md.md) properties.

  - Return a meaningful string that describes the **Dimension** with the [Description](description-property-ado-md.md) property.

  - Return the [Hierarchy](hierarchy-object-ado-md.md) objects that make up the **Dimension** with the [Hierarchies](hierarchies-collection-ado-md.md) collection.

  - Use the standard ADO [Properties](properties-collection-ado.md) collection to obtain additional information about the **Dimension** object.

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
<td><p>DefaultHierarchy</p></td>
<td><p>The unique name of the default hierarchy.</p></td>
</tr>
<tr class="even">
<td><p>Description</p></td>
<td><p>A meaningful description of the cube.</p></td>
</tr>
<tr class="odd">
<td><p>DimensionCaption</p></td>
<td><p>A label or caption associated with the dimension.</p></td>
</tr>
<tr class="even">
<td><p>DimensionCardinality</p></td>
<td><p>The number of members in the dimension.</p></td>
</tr>
<tr class="odd">
<td><p>DimensionGUID</p></td>
<td><p>The GUID of the dimension.</p></td>
</tr>
<tr class="even">
<td><p>DimensionName</p></td>
<td><p>The name of the dimension.</p></td>
</tr>
<tr class="odd">
<td><p>DimensionOrdinal</p></td>
<td><p>The ordinal number of the dimension among the group of dimensions that form the cube.</p></td>
</tr>
<tr class="even">
<td><p>DimensionType</p></td>
<td><p>The dimension type.</p></td>
</tr>
<tr class="odd">
<td><p>DimensionUniqueName</p></td>
<td><p>The unambiguous name of the dimension.</p></td>
</tr>
<tr class="even">
<td><p>SchemaName</p></td>
<td><p>The name of the schema to which this cube belongs.</p></td>
</tr>
</tbody>
</table>

