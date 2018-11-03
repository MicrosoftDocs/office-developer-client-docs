---
title: Delete method (ADO Fields Collection)
TOCTitle: Delete method (ADO Fields Collection)
ms:assetid: adc66365-703f-4491-fc5b-dbc9bca2ac53
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249817(v=office.15)
ms:contentKeyID: 48547047
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Delete method (ADO Fields Collection)


**Applies to**: Access 2013, Office 2013



Deletes an object from the [Fields](fields-collection-ado.md) collection.

## Syntax

*Fields*.Delete*Field*

## Parameters

- *Field*

  - A **Variant** that designates the [Field](field-object-ado.md) object to delete. This parameter can be the name of the **Field** object or the ordinal position of the **Field** object itself.

## Remarks

Calling the **Fields.Delete** method on an open [Recordset](recordset-object-ado.md) causes a run-time error.

