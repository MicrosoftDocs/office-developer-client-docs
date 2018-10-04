---
title: ActiveCommand Property (ADO)
TOCTitle: ActiveCommand Property (ADO)
ms:assetid: 41c19008-cbf7-ade9-b4ab-e908a16784ac
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249190(v=office.15)
ms:contentKeyID: 48544459
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ActiveCommand Property (ADO)


_**Applies to:** Access 2013 | Office 2013_

Indicates the [Command](command-object-ado.md) object that created the associated [Recordset](recordset-object-ado.md) object.

## Return Value

Returns a **Variant** that contains a **Command** object. Default is a null object reference.

## Remarks

The **ActiveCommand** property is read-only.

If a **Command** object was not used to create the current **Recordset**, then a **Null** object reference is returned.

Use this property to find the associated **Command** object when you are given only the resulting **Recordset** object.

