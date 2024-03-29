---
title: Supports method (ADO)
TOCTitle: Supports method (ADO)
ms:assetid: 2b4062ce-44df-4e84-1ce9-d6618c10c2af
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249059(v=office.15)
ms:contentKeyID: 48543924
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Supports method (ADO)

**Applies to**: Access 2013, Office 2013

Determines whether a specified [Recordset](recordset-object-ado.md) object supports a particular type of functionality.

## Syntax

*boolean* = *recordset*.Supports (*CursorOptions*)

## Return value

Returns a **Boolean** value that indicates whether all of the features identified by the *CursorOptions* argument are supported by the provider.

## Parameters

|Parameter|Description|
|:--------|:----------|
|*CursorOptions* |A **Long** expression that consists of one or more [CursorOptionEnum](cursoroptionenum.md) values.|

## Remarks

Use the **Supports** method to determine what types of functionality a **Recordset** object supports. If the **Recordset** object supports the features whose corresponding constants are in *CursorOptions*, the **Supports** method returns **True**. Otherwise, it returns **False**.


> [!NOTE]
> Although the **Supports** method may return **True** for a given functionality, it does not guarantee that the provider can make the feature available under all circumstances. The **Supports** method simply returns whether the provider can support the specified functionality, assuming certain conditions are met. For example, the **Supports** method may indicate that a **Recordset** object supports updates even though the cursor is based on a multiple table join, some columns of which are not updatable.


