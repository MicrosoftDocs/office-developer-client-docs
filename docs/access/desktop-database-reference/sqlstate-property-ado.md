---
title: SQLState Property (ADO)
TOCTitle: SQLState Property (ADO)
ms:assetid: cf3b078a-849e-1ad2-cba4-a26160080868
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250029(v=office.15)
ms:contentKeyID: 48547806
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SQLState Property (ADO)


**Applies to**: Access 2013, Office 2013

Indicates the SQL state for a given [Error](error-object-ado.md) object.

## Return Value

Returns a five-character **String** value that follows the ANSI SQL standard and indicates the error code.

## Remarks

Use the **SQLState** property to read the five-character error code that the provider returns when an error occurs during the processing of an SQL statement. For example, when using the Microsoft OLE DB Provider for ODBC with a Microsoft SQL Server database, SQL state error codes originate from ODBC, based either on errors specific to ODBC or on errors that originate from Microsoft SQL Server, and are then mapped to ODBC errors. These error codes are documented in the ANSI SQL standard, but may be implemented differently by different data sources.

