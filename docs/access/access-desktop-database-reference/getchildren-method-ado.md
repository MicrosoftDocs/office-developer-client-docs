---
title: GetChildren Method (ADO)
TOCTitle: GetChildren Method (ADO)
ms:assetid: 998cf640-ffc7-51e1-4d1e-4797f7cdea4a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249687(v=office.15)
ms:contentKeyID: 48546515
ms.date: 09/18/2015
mtps_version: v=office.15
---

# GetChildren Method (ADO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Return Value  
Remarks  

Returns a [Recordset](recordset-object-ado.md) whose rows represent the children of a collection [Record](record-object-ado.md).

## Syntax

**Set** *recordset* = *record*.GetChildren

## Return Value

A **Recordset** object for which each row represents a child of the current **Record** object. For example, the children of a **Record** that represents a directory would be the files and subdirectories contained within the parent directory.

## Remarks

The provider determines what columns exist in the returned **Recordset**. For example, a document source provider always returns a resource **Recordset**.

