---
title: Parameters Collection (ADO)
TOCTitle: Parameters Collection (ADO)
ms:assetid: 554387c3-3572-5391-3b24-c7d3443844cd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249283(v=office.15)
ms:contentKeyID: 48544923
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- ado210.chm1231103
f1_categories:
- Office.Version=v15
---

# Parameters Collection (ADO)


_**Applies to:** Access 2013 | Office 2013_

Contains all the [Parameter](parameter-object-ado.md) objects of a [Command](command-object-ado.md) object.

## Remarks

A **Command** object has a **Parameters** collection made up of **Parameter** objects.

Using the [Refresh](refresh-method-ado.md) method on a **Command** object's **Parameters** collection retrieves provider parameter information for the stored procedure or parameterized query specified in the **Command** object. Some providers do not support stored procedure calls or parameterized queries; calling the **Refresh** method on the **Parameters** collection when using such a provider will return an error.

If you have not defined your own **Parameter** objects and you access the **Parameters** collection before calling the **Refresh** method, ADO will automatically call the method and populate the collection for you.

You can minimize calls to the provider to improve performance if you know the properties of the parameters associated with the stored procedure or parameterized query you wish to call. Use the [CreateParameter](createparameter-method-ado.md) method to create **Parameter** objects with the appropriate property settings and use the [Append](append-method-ado.md) method to add them to the **Parameters** collection. This lets you set and return parameter values without having to call the provider for the parameter information. If you are writing to a provider that does not supply parameter information, you must manually populate the **Parameters** collection using this method to be able to use parameters at all. Use the [Delete](delete-method-ado-parameters-collection.md) method to remove **Parameter** objects from the **Parameters** collection if necessary.

The objects in the **Parameters** collection of a **Recordset** go out of scope (therefore becoming unavailable) when the **Recordset** is closed.

