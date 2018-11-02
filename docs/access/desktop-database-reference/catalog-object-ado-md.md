---
title: Catalog object (ADO MD)
TOCTitle: Catalog object (ADO MD)
ms:assetid: 708c4082-3589-7f3b-5ea3-f3705f3d3ff1
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249445(v=office.15)
ms:contentKeyID: 48545559
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Catalog object (ADO MD)


**Applies to**: Access 2013, Office 2013

Contains multidimensional schema information (that is, cubes and underlying dimensions, hierarchies, levels, and members) specific to a multidimensional data provider (MDP).

## Remarks

With the collections and properties of a **Catalog** object, you can do the following:

  - Open the catalog by setting the [ActiveConnection](activeconnection-property-ado-md.md) property to a standard ADO [Connection](connection-object-ado.md) object or to a valid connection string.

  - Identify the **Catalog** with the [Name](name-property-ado-md.md) property.

  - Iterate through the cubes in a catalog using the [CubeDefs](cubedefs-collection-ado-md.md) collection.

