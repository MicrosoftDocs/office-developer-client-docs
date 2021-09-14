---
title: CancelUpdate method (RDS)
TOCTitle: CancelUpdate method (RDS)
ms:assetid: 373a3feb-125d-915a-fd56-d4b04b20db54
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249130(v=office.15)
ms:contentKeyID: 48544188
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# CancelUpdate method (RDS)

**Applies to**: Access 2013, Office 2013

Cancels any changes made to the current or new row of a [Recordset](recordset-object-ado.md) object.

## Syntax

*DataControl*.CancelUpdate

## Parameters

|Parameter|Description|
|:--------|:----------|
|*DataControl* |An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object.|

## Remarks

The Cursor Service for OLE DB keeps both a copy of the original values and a cache of changes. When you call **CancelUpdate**, the cache of changes is reset to empty, and any bound controls are refreshed with the original data.

