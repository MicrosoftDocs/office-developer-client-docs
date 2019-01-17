---
title: Delete method (ADO Parameters Collection)
TOCTitle: Delete method (ADO Parameters Collection)
ms:assetid: 03ffc24d-fea2-30fa-c8e9-43eb524fd51f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248804(v=office.15)
ms:contentKeyID: 48542998
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Delete method (ADO Parameters Collection)

**Applies to**: Access 2013, Office 2013

Deletes an object from the [Parameters](parameters-collection-ado.md) collection.

## Syntax

*Parameters*.Delete *Index*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Index* |A **String** value that contains the name of the object you want to delete, or the objects ordinal position (index) in the collection.|

## Remarks

Using the **Delete** method on a collection lets you remove one of the objects in the collection. This method is available only on the **Parameters** collection of a [Command](command-object-ado.md) object. You must use the [Parameter](parameter-object-ado.md) object's [Name](name-property-ado.md) property or its collection index when calling the **Delete** method — an object variable is not a valid argument.

