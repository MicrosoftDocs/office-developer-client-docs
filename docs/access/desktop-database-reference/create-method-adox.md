---
title: Create method (ADOX)
TOCTitle: Create method (ADOX)
ms:assetid: d4072ee7-a0b9-7780-7be0-1d64b42b437c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250060(v=office.15)
ms:contentKeyID: 48547924
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Create method (ADOX)

**Applies to**: Access 2013, Office 2013

Creates a new catalog.

## Syntax

*Catalog*.Create*ConnectString*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*ConnectString* |A **String** value used to connect to the data source.|

## Remarks

The **Create** method creates and opens a new ADO [Connection](connection-object-ado.md) to the data source specified in *ConnectString*. If successful, the new **Connection** object is assigned to the [ActiveConnection](activeconnection-property-adox.md) property.

An error will occur if the provider does not support creating new catalogs.

