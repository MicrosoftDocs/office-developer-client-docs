---
title: CubeDef Object (ADO MD)
TOCTitle: CubeDef Object (ADO MD)
ms:assetid: 199235b7-3d98-f655-27bc-94f66e994e06
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248941(v=office.15)
ms:contentKeyID: 48543502
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CubeDef Object (ADO MD)


**Applies to**: Access 2013 | Office 2013

Represents a cube from a multidimensional schema, containing a set of related dimensions.

## Remarks

With the collections and properties of a **CubeDef** object, you can do the following:

  - Identify a **CubeDef** with the [Name](name-property-ado-md.md) property.

  - Return a string that describes the cube with the [Description](description-property-ado-md.md) property.

  - Return the dimensions that make up the cube with the [Dimensions](dimensions-collection-ado-md.md) collection.

  - Obtain additional information about the **CubeDef** with the standard ADO [Properties](properties-collection-ado.md) collection.

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
<td><p>CreatedOn</p></td>
<td><p>Date and time of cube creation.</p></td>
</tr>
<tr class="odd">
<td><p>CubeGUID</p></td>
<td><p>Cube GUID.</p></td>
</tr>
<tr class="even">
<td><p>CubeName</p></td>
<td><p>The name of the cube.</p></td>
</tr>
<tr class="odd">
<td><p>CubeType</p></td>
<td><p>The type of the cube.</p></td>
</tr>
<tr class="even">
<td><p>DataUpdatedBy</p></td>
<td><p>User ID of the person doing the last data update.</p></td>
</tr>
<tr class="odd">
<td><p>Description</p></td>
<td><p>A meaningful description of the cube.</p></td>
</tr>
<tr class="even">
<td><p>LastSchemaUpdate</p></td>
<td><p>Date and time of last schema update.</p></td>
</tr>
<tr class="odd">
<td><p>SchemaName</p></td>
<td><p>The name of the schema to which this cube belongs.</p></td>
</tr>
<tr class="even">
<td><p>SchemaUpdatedBy</p></td>
<td><p>User ID of the person doing the last schema update.</p></td>
</tr>
</tbody>
</table>

