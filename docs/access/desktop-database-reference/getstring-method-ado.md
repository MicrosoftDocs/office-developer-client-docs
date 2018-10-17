---
title: GetString Method (ADO)
TOCTitle: GetString Method (ADO)
ms:assetid: f496305e-a1f5-7014-7808-7e4961e5f0fa
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250242(v=office.15)
ms:contentKeyID: 48548693
ms.date: 09/18/2015
mtps_version: v=office.15
---

# GetString Method (ADO)


**Applies to**: Access 2013 | Office 2013


Returns the [Recordset](recordset-object-ado.md) as a string.

## Syntax

*Variant* = *recordset*.GetString(*StringFormat*, *NumRows*, *ColumnDelimiter*, *RowDelimiter*, *NullExpr*)

## Return value

Returns the **Recordset** as a string-valued **Variant** (BSTR).

## Parameters

  - *StringFormat*

  - A [StringFormatEnum](stringformatenum.md) value that specifies how the **Recordset** should be converted to a string. The *RowDelimiter*, *ColumnDelimiter*, and *NullExpr* parameters are used only with a *StringFormat* of **adClipString**.

  - *NumRows*

  - Optional. The number of rows to be converted in the **Recordset**. If *NumRows* is not specified, or if it is greater than the total number of rows in the **Recordset**, then all the rows in the **Recordset** are converted.

  - *ColumnDelimiter*

  - Optional. A delimiter used between columns, if specified, otherwise the TAB character.

  - *RowDelimiter*

  - Optional. A delimiter used between rows, if specified, otherwise the CARRIAGE RETURN character.

  - *NullExpr*

  - Optional. An expression used in place of a null value, if specified, otherwise the empty string.

## Remarks

Row data, but no schema data, is saved to the string. Therefore, a **Recordset** cannot be reopened using this string.

This method is equivalent to the RDO **GetClipString** method.

