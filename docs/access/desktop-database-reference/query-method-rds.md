---
title: Query method (RDS - Access desktop database reference)
TOCTitle: Query method (RDS)
ms:assetid: c88d82bd-2139-7f1e-4e5e-9030f3795816
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249975(v=office.15)
ms:contentKeyID: 48547658
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Query method (RDS)

**Applies to**: Access 2013, Office 2013

Uses a valid SQL query string to return a [Recordset](recordset-object-ado.md).

## Syntax

Set*Recordset* = *DataFactory*.Query(*Connection*, *Query*)

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Recordset* |An object variable that represents a **Recordset** object.|
|*DataFactory* |An object variable that represents an [RDSServer.DataFactory](datafactory-object-rdsserver.md) object.|
|*Connection* |A **String** value that contains the server connection information. This is similar to the [Connect](connect-property-rds.md) property.|
|*Query* |A **String** that contains the SQL query.|

## Remarks

The query should use the SQL dialect of the database server. A result status is returned if there is an error with the query that was executed. The **Query** method doesn't perform any syntax checking on the **Query** string.

