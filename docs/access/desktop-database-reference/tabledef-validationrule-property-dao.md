---
title: TableDef.ValidationRule property (DAO)
TOCTitle: ValidationRule Property
ms:assetid: 7dcd6f2c-45bc-a50b-727d-589371d5803f
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196425(v=office.15)
ms:contentKeyID: 48545864
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052925
f1_categories:
- Office.Version=v15
---

# TableDef.ValidationRule property (DAO)

**Applies to**: Access 2013, Office 2013

Sets or returns a value that validates the data in a field as it's changed or added to a table (Microsoft Access workspaces only).Read/write **String**.

## Syntax

*expression* .ValidationRule

*expression* A variable that represents a **TableDef** object.

## Remarks

The settings or return values is a **String** that describes a comparison in the form of an SQL WHERE clause without the WHERE reserved word. For an object not yet appended to the **Fields** collection, this property is read/write.

The **ValidationRule** property determines whether or not a field contains valid data. If the data is not valid, a trappable run-time error occurs. The returned error message is the text of the **ValidationText** property, if specified, or the text of the expression specified by **ValidationRule**.

Validation is supported only for databases that use the Microsoft Access database engine.

The string expression specified by the **ValidationRule** property of a **Field** object can refer only to that **Field**. The expression can't refer to user-defined functions, SQL aggregate functions, or queries. To set a **Field** object's **ValidationRule** property when its **ValidateOnSet** property setting is **True**, the expression must successfully parse (with the field name as an implied operand) and evaluate to **True**. If its **ValidateOnSet** property setting is **False**, the **ValidationRule** property setting is ignored.

The **ValidationRule** property of a **Recordset** or **TableDef** object can refer to multiple fields in that object. The restrictions noted earlier in this topic for the **Field** object apply.

For a **TableDef** object based on an linked table, the **ValidationRule** property inherits the **ValidationRule** property setting of the underlying base table. If the underlying base table doesn't support validation, the value of this property is a zero-length string ("").

> [!NOTE]
> If you set the property to a string concatenated with a non-integer value, and the system parameters specify a non-U.S. decimal character such as a comma (for example, strRule = "PRICE &gt; " &amp; lngPrice, and lngPrice = 125,50), an error will result when your code attempts to validate any data. This is because during concatenation, the number will be converted to a string using your system's default decimal character, and Microsoft Access SQL only accepts U.S. decimal characters.