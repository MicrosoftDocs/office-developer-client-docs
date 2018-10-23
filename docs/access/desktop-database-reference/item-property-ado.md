---
title: Item Property (ADO)
TOCTitle: Item Property (ADO)
ms:assetid: 793c305f-0e5b-a529-e21f-b7ab0843ed49
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249499(v=office.15)
ms:contentKeyID: 48545767
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Item Property (ADO)

**Applies to**: Access 2013, Office 2013

Indicates a specific member of a collection, by name or ordinal number.

## Syntax

Set*object* = *collection*.Item ( Index )

## Return Value

Returns an object reference.

## Parameters

- *Index*

- A **Variant** expression that evaluates either to the name or to the ordinal number of an object in a collection.

## Remarks

Use the **Item** property to return a specific object in a collection. If **Item** cannot find an object in the collection corresponding to the *Index* argument, an error occurs. Also, some collections don't support named objects; for these collections, you must use ordinal number references.

The **Item** property is the default property for all collections; therefore, the following syntax forms are interchangeable:

```vb
    collection.Item (Index)
    collection (Index)
```
