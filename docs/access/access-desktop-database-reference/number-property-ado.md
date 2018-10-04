---
title: Number Property (ADO)
TOCTitle: Number Property (ADO)
ms:assetid: b5103af5-356b-ec74-cd62-86e59467d491
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249868(v=office.15)
ms:contentKeyID: 48547243
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Number Property (ADO)


_**Applies to:** Access 2013 | Office 2013_

Indicates the number that uniquely identifies an [Error](error-object-ado.md) object.

## Return Value

Returns a **Long** value that may correspond to one of the [ErrorValueEnum](errorvalueenum.md) constants.

## Remarks

Use the **Number** property to determine which error occurred. The value of the property is a unique number that corresponds to the error condition.

The [Errors](errors-collection-ado.md) collection returns an HRESULT in either hexadecimal format (for example, 0x80004005) or long value (for example, 2147467259). These HRESULTs can be raised by underlying components, such as OLE DB or even OLE itself. For more information about these numbers, see Chapter 16 of the *OLE DB Programmer's Reference.*

