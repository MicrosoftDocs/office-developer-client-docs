---
title: Recordset2.Filter property (DAO)
TOCTitle: Filter Property
ms:assetid: 5b3b4e18-8af4-5acd-a129-513ba2d913d1
ms:mtpsurl: https://msdn.microsoft.com/library/Ff194529(v=office.15)
ms:contentKeyID: 48545069
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053062
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# Recordset2.Filter property (DAO)


**Applies to**: Access 2013, Office 2013

Sets or returns a value that determines the records included in a subsequently opened **Recordset** object (Microsoft Access workspaces only). Read/write **String**.

## Syntax

*expression* .Filter

*expression* An expression that returns a **Recordset2** object.

## Remarks

The setting or return value is a String data type that contains the WHERE clause of an SQL statement without the reserved word WHERE.

Use the **Filter** property to apply a filter to a dynaset–, snapshot–, or forward–only–type **Recordset** object.

You can use the **Filter** property to restrict the records returned from an existing object when a new **Recordset** object is opened based on an existing **Recordset** object.

Use the U.S. date format (month-day-year) when you filter fields containing dates, even if you're not using the U.S. version of the Microsoft Access database engine (in which case you must assemble any dates by concatenating strings, for example, strMonth & "-" & strDay & "-" & strYear). Otherwise, the data may not be filtered as you expect.

In many cases, it's faster to open a new **Recordset** object by using an SQL statement that includes a WHERE clause.

If you set the property to a string concatenated with a non–integer value, and the system parameters specify a non-U.S. decimal character such as a comma (for example, strFilter = "PRICE \> " & lngPrice, and lngPrice = 125,50), an error occurs when you try to open the next **Recordset**. This is because during concatenation, the number will be converted to a string using your system's default decimal character, and Microsoft Access SQL only accepts U.S. decimal characters.

