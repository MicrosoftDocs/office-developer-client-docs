---
title: Cell object (ADO MD)
TOCTitle: Cell object (ADO MD)
ms:assetid: b9d00b71-1f40-5bd1-4b89-fbdb59c552ba
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249892(v=office.15)
ms:contentKeyID: 48547356
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Cell object (ADO MD)


**Applies to**: Access 2013, Office 2013

Represents the data at the intersection of axis coordinates contained in a cellset.

## Remarks

A **Cell** object is returned by the [Item](item-property-ado-md-cellset.md) property of a [Cellset](cellset-object-ado-md.md) object.

With the collections and properties of a **Cell** object, you can do the following:

  - Return the data in the **Cell** with the [Value](value-property-ado-md.md) property.

  - Return the string representing the formatted display of the **Value** property with the [FormattedValue](formattedvalue-property-ado-md.md) property.

  - Return the ordinal value of the **Cell** within the **Cellset** with the [Ordinal](ordinal-property-ado-md-cell.md) property.

  - Determine the position of the **Cell** within the [CubeDef](cubedef-object-ado-md.md) with the [Positions](positions-collection-ado-md.md) collection.

  - Retrieve other information about the **Cell** with the standard ADO [Properties](properties-collection-ado.md) collection.

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
<td><p>BackColor</p></td>
<td><p>Background color used when displaying the cell.</p></td>
</tr>
<tr class="even">
<td><p>FontFlags</p></td>
<td><p>Bitmask detailing effects on the font.</p></td>
</tr>
<tr class="odd">
<td><p>FontName</p></td>
<td><p>Font used to display the cell value.</p></td>
</tr>
<tr class="even">
<td><p>FontSize</p></td>
<td><p>Font size used to display the cell value.</p></td>
</tr>
<tr class="odd">
<td><p>ForeColor</p></td>
<td><p>Foreground color used when displaying the cell.</p></td>
</tr>
<tr class="even">
<td><p>FormatString</p></td>
<td><p>Value in a formatted string.</p></td>
</tr>
</tbody>
</table>

