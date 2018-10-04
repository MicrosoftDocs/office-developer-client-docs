---
title: Field2.Value Property (DAO)
TOCTitle: Value Property
ms:assetid: 6ead6ba8-1613-99c7-7968-56f5b81b2385
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff195566(v=office.15)
ms:contentKeyID: 48545515
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Field2.Value Property (DAO)


**Applies to**: Access 2013 | Office 2013

Sets or returns the value of an object. Read/write **Variant**.

## Syntax

*expression* .Value

*expression* A variable that represents a **Field2** object.

## Remarks

The setting or return value is a Variant data type that evaluates to a value appropriate for the data type, as specified by the **Type** property of an object.

Generally, the **Value** property is used to retrieve and alter data in **Recordset** objects.

The **Value** property is the default property of the **Field2**, **Parameter**, and **Property** objects. Therefore, you can set or return the value of one of these objects by referring to them directly instead of specifying the **Value** property.

Trying to set or return the **Value** property in an inappropriate context (for example, the **Value** property of a **Field2** object in the **Fields** collection of a **TableDef** object) will cause a trappable error.


> [!NOTE]
> <P>When reading decimal values from a Microsoft SQL Server database, they will be formatted using scientific notation through a Microsoft Access workspace, but will appear as normal decimal values through an ODBCDirect workspace.</P>


