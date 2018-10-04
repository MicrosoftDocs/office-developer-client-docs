---
title: Recordset2.StillExecuting Property (DAO)
TOCTitle: StillExecuting Property
ms:assetid: f051c350-0451-44fe-0e47-b152bae4b481
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff836546(v=office.15)
ms:contentKeyID: 48548601
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset2.StillExecuting Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

## Syntax

*expression* .StillExecuting

*expression* A variable that represents a **Recordset2** object.

## Remarks

Use the **StillExecuting** property to determine if the most recently called asynchronous **Execute** or **OpenConnection** method (that is, a method executed with the **dbRunAsync** option) is complete. While the **StillExecuting** property is **True**, any returned object cannot be accessed.

Once the **StillExecuting** property returns **False**, following the **OpenConnection** call that returns the associated **Connection** object, the object can be referenced. So long as **StillExecuting** remains **True**, the object may not be referenced, other than to read the **StillExecuting** property.

Use the **[Cancel](connection-cancel-method-dao.md)** method to terminate execution of a task in progress.

