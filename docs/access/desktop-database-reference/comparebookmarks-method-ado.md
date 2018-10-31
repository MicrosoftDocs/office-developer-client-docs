---
title: CompareBookmarks Method (ADO)
TOCTitle: CompareBookmarks Method (ADO)
ms:assetid: 826cb3c7-2f5c-284f-421d-6b7b07f14dec
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249564(v=office.15)
ms:contentKeyID: 48545977
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CompareBookmarks Method (ADO)


**Applies to**: Access 2013 | Office 2013

Compares two bookmarks and returns an indication of their relative values.

## Syntax

*result* = *recordset*.CompareBookmarks(*Bookmark1*, *Bookmark2*)

## Return value

Returns a [CompareEnum](compareenum.md) value that indicates the relative row position of two records represented by their bookmarks.

## Parameters

  - *Bookmark1*

  - The bookmark of the first row.

  - *Bookmark2*

  - The bookmark of the second row.

## Remarks

The bookmarks must apply to the same [Recordset](recordset-object-ado.md) object, or a **Recordset** object and its [clone](clone-method-ado.md). You cannot reliably compare bookmarks from different **Recordset** objects, even if they were created from the same source or command. Nor can you compare bookmarks for a **Recordset** object whose underlying provider does not support comparisons.

A bookmark uniquely identifies a row in a **Recordset** object. Use the current row's [Bookmark](bookmark-property-ado.md) property to obtain its bookmark.

Because the data type of a bookmark is provider specific, ADO exposes it as a Variant. For example, SQL Server bookmarks are of type DBTYPE\_R8 (Double). ADO would expose this type as a Variant with a subtype of Double.

When comparing bookmarks, ADO does not attempt any type of coercion. The values are simply passed to the provider where the compare occurs. If bookmarks passed to the **CompareBookmarks** method are stored in variables of differing types, it can generate the type mismatch error, "Arguments are of the wrong type, are out of the acceptable range, or are in conflict with each other."

A bookmark that is not valid or incorrectly formed will cause an error.

