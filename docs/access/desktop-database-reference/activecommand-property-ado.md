---
title: ActiveCommand property (ADO)
TOCTitle: ActiveCommand property (ADO)
ms:assetid: 41c19008-cbf7-ade9-b4ab-e908a16784ac
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249190(v=office.15)
ms:contentKeyID: 48544459
ms.date: 10/17/2018
mtps_version: v=office.15
localization_priority: Normal
---

# ActiveCommand property (ADO)

**Applies to**: Access 2013, Office 2013

Indicates the [Command](command-object-ado.md) object that created the associated [Recordset](recordset-object-ado.md) object.

## Return value

Returns a **Variant** that contains a **Command** object. Default is a null object reference.

## Remarks

The **ActiveCommand** property is read-only.

If a **Command** object was not used to create the current **Recordset**, a **Null** object reference is returned.

Use this property to find the associated **Command** object when you are given only the resulting **Recordset** object.

