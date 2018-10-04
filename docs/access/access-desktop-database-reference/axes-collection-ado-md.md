﻿---
title: Axes Collection (ADO MD)
TOCTitle: Axes Collection (ADO MD)
ms:assetid: 7c719197-45f1-a5b9-665d-25cb693b1eb0
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249520(v=office.15)
ms:contentKeyID: 48545836
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Axes Collection (ADO MD)


**Applies to**: Access 2013 | Office 2013

Contains the [Axis](axis-object-ado-md.md) objects that define a cellset.

## Remarks

A [Cellset](cellset-object-ado-md.md) object contains an **Axes** collection. Once the **Cellset** is opened, this collection will contain at least one **Axis**. See the [Axis](axis-object-ado-md.md) object for a more detailed explanation of how to use **Axis** objects.


> [!NOTE]
> <P>The filter axis of a <STRONG>Cellset</STRONG> is not contained in the <STRONG>Axes</STRONG> collection. See the <A href="filteraxis-property-ado-md.md">FilterAxis</A> property for more information.</P>



**Axes** is a standard ADO collection. With the properties and methods of a collection, you can do the following:

  - Obtain the number of objects in the collection with the [Count](count-property-ado.md) property.

  - Return an object from the collection with the default [Item](item-property-ado.md) property.

  - Update the objects in the collection from the provider with the [Refresh](refresh-method-ado.md) method.

