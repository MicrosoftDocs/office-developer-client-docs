---
title: Recordset.StillExecuting Property (DAO)
TOCTitle: StillExecuting Property
ms:assetid: 0e53c98f-17ac-3569-d780-540a6932013e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff845245(v=office.15)
ms:contentKeyID: 48543245
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset.StillExecuting Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

## Syntax

*expression* .StillExecuting

*expression* A variable that represents a **Recordset** object.

## Remarks

Use the **StillExecuting** property to determine if the most recently called asynchronous **Execute** or **OpenConnection** method (that is, a method executed with the **dbRunAsync** option) is complete. While the **StillExecuting** property is **True**, any returned object cannot be accessed.

Once the **StillExecuting** property returns **False**, following the **OpenConnection** call that returns the associated **Connection** object, the object can be referenced. So long as **StillExecuting** remains **True**, the object may not be referenced, other than to read the **StillExecuting** property.

Use the **[Cancel](connection-cancel-method-dao.md)** method to terminate execution of a task in progress.

