---
title: NativeError Property (ADO)
TOCTitle: NativeError Property (ADO)
ms:assetid: 9f4d4064-5ee7-20f8-fd54-2cb2eae64d7b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249731(v=office.15)
ms:contentKeyID: 48546685
ms.date: 09/18/2015
mtps_version: v=office.15
---

# NativeError Property (ADO)


**Applies to**: Access 2013 | Office 2013

Indicates the provider-specific error code for a given [Error](error-object-ado.md) object.

## Return Value

Returns a **Long** value that indicates the error code.

## Remarks

Use the **NativeError** property to retrieve the database-specific error information for a particular **Error** object. For example, when using the Microsoft ODBC Provider for OLE DB with a Microsoft SQL Server database, native error codes that originate from SQL Server pass through ODBC and the ODBC Provider to the ADO **NativeError** property.

