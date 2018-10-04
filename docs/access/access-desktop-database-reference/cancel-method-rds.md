---
title: Cancel Method (RDS)
TOCTitle: Cancel Method (RDS)
ms:assetid: 08f667c2-7a3f-c2e7-7bdf-3eb533defa33
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248827(v=office.15)
ms:contentKeyID: 48543109
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Cancel Method (RDS)


**Applies to**: Access 2013 | Office 2013

Cancels execution of a pending, asynchronous method call.

## Syntax

*RDS*. *DataControl*.Cancel

## Remarks

When you call **Cancel**, [ReadyState](readystate-property-rds.md) is automatically set to **adcReadyStateLoaded**, and the [Recordset](recordset-object-ado.md) will be empty.

