---
title: Member Object (ADO MD)
TOCTitle: Member Object (ADO MD)
ms:assetid: d80c024a-07dc-7a35-f8f2-b4d5b19d89e4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250088(v=office.15)
ms:contentKeyID: 48548025
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Member Object (ADO MD)


**Applies to**: Access 2013 | Office 2013

Represents a member of a level in a cube, the children of a member of a level, or a member of a position along an axis of a cellset.

## Remarks

The properties of a **Member** differ depending on the context in which it is used. A **Member** of a [Level](level-object-ado-md.md) in a [CubeDef](cubedef-object-ado-md.md) has a [Children](children-property-ado-md.md) property that returns the **Members** on the next lower level in the hierarchy from the current **Member**. For a **Member** of a [Position](position-object-ado-md.md), the **Children** collection is always empty. Also, the [Type](type-property-ado-md.md) property applies only to **Members** of a **Level**.

A **Member** of **Position** has two properties — [DrilledDown](drilleddown-property-ado-md.md) and [ParentSameAsPrev](parentsameasprev-property-ado-md.md) — that are useful when displaying the [Cellset](cellset-object-ado-md.md). An error will occur if these properties are accessed on a **Member** of a **Level**.

With the collections and properties of a **Member** object of a **Level**, you can do the following:

  - Identify the **Member** with the [Name](name-property-ado-md.md) and [UniqueName](uniquename-property-ado-md.md) properties.

  - Return a string to use when displaying the **Member** with the [Caption](caption-property-ado-md.md) property.

  - Return a meaningful string that describes a measure or formula **Member** with the [Description](description-property-ado-md.md) property.

  - Determine the nature of the **Member** with the [Type](type-property-ado-md.md) property.

  - Obtain information about the **Level** of the **Member** with the [LevelDepth](leveldepth-property-ado-md.md) and [LevelName](levelname-property-ado-md.md) properties.

  - Obtain related **Members** in a [Hierarchy](hierarchy-object-ado-md.md) with the [Parent](parent-property-ado-md.md) and [Children](children-property-ado-md.md) properties.

  - Count the children of a **Member** with the [ChildCount](childcount-property-ado-md.md) property.

  - Use the standard ADO [Properties](properties-collection-ado.md) collection to obtain additional information about the **Level** object.

With the collections and properties of a **Member** of a **Position** along an [Axis](axis-object-ado-md.md), you can do the following:

  - Identify the **Member** with the [Name](name-property-ado-md.md) and [UniqueName](uniquename-property-ado-md.md) properties.

  - Return a string to use when displaying the **Member** with the [Caption](caption-property-ado-md.md) property.

  - Return a meaningful string that describes a measure or formula **Member** with the [Description](description-property-ado-md.md) property.

  - Obtain information about the **Level** of the **Member** with the [LevelDepth](leveldepth-property-ado-md.md) and [LevelName](levelname-property-ado-md.md) properties.

  - Count the children of a **Member** with the [ChildCount](childcount-property-ado-md.md) property.

  - Use the [DrilledDown](drilleddown-property-ado-md.md) property to determine whether there is at least one child on the **Axis** immediately following this **Member**.

  - Use the [ParentSameAsPrev](parentsameasprev-property-ado-md.md) property to determine whether the parent of this **Member** is the same as the parent of the immediately preceding **Member**.

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
<td><p>ChildrenCardinality</p></td>
<td><p>The number of children that the member has.</p></td>
</tr>
<tr class="odd">
<td><p>CubeName</p></td>
<td><p>The name of the cube.</p></td>
</tr>
<tr class="even">
<td><p>Description</p></td>
<td><p>A meaningful description of the member.</p></td>
</tr>
<tr class="odd">
<td><p>DimensionUniqueName</p></td>
<td><p>The unambiguous name of the <a href="dimension-object-ado-md.md">dimension</a>.</p></td>
</tr>
<tr class="even">
<td><p>HierarchyUniqueName</p></td>
<td><p>The unambiguous name of the hierarchy.</p></td>
</tr>
<tr class="odd">
<td><p>LevelNumber</p></td>
<td><p>The distance between the level and the root of the hierarchy.</p></td>
</tr>
<tr class="even">
<td><p>LevelUniqueName</p></td>
<td><p>The unambiguous name of the level.</p></td>
</tr>
<tr class="odd">
<td><p>MemberCaption</p></td>
<td><p>A label or caption associated with the member.</p></td>
</tr>
<tr class="even">
<td><p>MemberGUID</p></td>
<td><p>The GUID of the member.</p></td>
</tr>
<tr class="odd">
<td><p>MemberName</p></td>
<td><p>The name of the member.</p></td>
</tr>
<tr class="even">
<td><p>MemberOrdinal</p></td>
<td><p>The ordinal number of the member.</p></td>
</tr>
<tr class="odd">
<td><p>MemberType</p></td>
<td><p>The type of the member.</p></td>
</tr>
<tr class="even">
<td><p>MemberUniqueName</p></td>
<td><p>The unambiguous name of the member.</p></td>
</tr>
<tr class="odd">
<td><p>ParentCount</p></td>
<td><p>The count of the number of parents that this member has.</p></td>
</tr>
<tr class="even">
<td><p>ParentLevel</p></td>
<td><p>The level number of the member's parent.</p></td>
</tr>
<tr class="odd">
<td><p>ParentUniqueName</p></td>
<td><p>The unambiguous name of the member's parent.</p></td>
</tr>
<tr class="even">
<td><p>SchemaName</p></td>
<td><p>The name of the schema to which this cube belongs.</p></td>
</tr>
</tbody>
</table>

