﻿---
title: Parameter Object (ADO)
TOCTitle: Parameter Object (ADO)
ms:assetid: 7577598e-3d0c-30c6-5f24-1cfe98791798
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249481(v=office.15)
ms:contentKeyID: 48545676
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Parameter Object (ADO)


**Applies to**: Access 2013 | Office 2013

Represents a parameter or argument associated with a [Command](command-object-ado.md) object based on a parameterized query or stored procedure.

## Remarks

Many providers support parameterized commands. These are commands in which the desired action is defined once, but variables (or parameters) are used to alter some details of the command. For example, an SQL SELECT statement could use a parameter to define the matching criteria of a WHERE clause, and another to define the column name for a SORT BY clause.

**Parameter** objects represent parameters associated with parameterized queries, or the in/out arguments and the return values of stored procedures. Depending on the functionality of the provider, some collections, methods, or properties of a **Parameter** object may not be available.

With the collections, methods, and properties of a **Parameter** object, you can do the following:

  - Set or return the name of a parameter with the [Name](name-property-ado.md) property.

  - Set or return the value of a parameter with the [Value](value-property-ado.md) property. **Value** is the default property of the **Parameter** object.

  - Set or return parameter characteristics with the [Attributes](attributes-property-ado.md), [Direction](direction-property-ado.md), [Precision](precision-property-ado.md), [NumericScale](numericscale-property-ado.md), [Size](size-property-ado.md), and [Type](type-property-ado.md) properties.

  - Pass long binary or character data to a parameter with the [AppendChunk](appendchunk-method-ado.md) method.

  - Access provider-specific attributes with the [Properties](properties-collection-ado.md) collection.

If you know the names and properties of the parameters associated with the stored procedure or parameterized query you wish to call, you can use the [CreateParameter](createparameter-method-ado.md) method to create **Parameter** objects with the appropriate property settings and use the [Append](append-method-ado.md) method to add them to the [Parameters](parameters-collection-ado.md) collection. This lets you set and return parameter values without having to call the [Refresh](refresh-method-ado.md) method on the **Parameters** collection to retrieve the parameter information from the provider, a potentially resource-intensive operation.

