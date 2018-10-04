---
title: Axis Object (ADO MD)
TOCTitle: Axis Object (ADO MD)
ms:assetid: a4332b69-8900-08f1-a4e2-9395d005ed42
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249763(v=office.15)
ms:contentKeyID: 48546807
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Axis Object (ADO MD)


_**Applies to:** Access 2013 | Office 2013_

Represents a positional or filter axis of a cellset, containing selected members of one or more dimensions.

## Remarks

An **Axis** object can be contained by an [Axes](axes-collection-ado-md.md) collection, or returned by the [FilterAxis](filteraxis-property-ado-md.md) property of a [Cellset](cellset-object-ado-md.md).

With the collections and properties of an **Axis** object, you can do the following:

  - Identify the **Axis** with the [Name](name-property-ado-md.md) property.

  - Iterate through each position along an **Axis** using the [Positions](positions-collection-ado-md.md) collection.

  - Obtain the number of dimensions on the **Axis** with the [DimensionCount](dimensioncount-property-ado-md.md) property.

  - Obtain provider-specific attributes of the **Axis** with the standard ADO [Properties](properties-collection-ado.md) collection.

