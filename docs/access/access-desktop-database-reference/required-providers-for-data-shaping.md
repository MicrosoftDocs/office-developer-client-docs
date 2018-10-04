---
title: Required Providers for Data Shaping
TOCTitle: Required Providers for Data Shaping
ms:assetid: eb8933fb-d533-3ea7-e045-35c1ca585765
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250194(v=office.15)
ms:contentKeyID: 48548488
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Required Providers for Data Shaping


_**Applies to:** Access 2013 | Office 2013_

Data shaping typically requires two providers. The service provider, [Data Shaping Service for OLE DB](microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), supplies the data shaping functionality, and a data provider, such as the OLE DB Provider for SQL Server, supplies rows of data to populate the shaped [Recordset](recordset-object-ado.md).

The name of the service provider (MSDataShape) can be specified as the value of the [Connection](connection-object-ado.md) object [Provider](provider-property-ado.md) property or the connection string keyword "Provider=MSDataShape;".

The name of the data provider can be specified as the value of the **Data Provider** dynamic property, which is added to the **Connection** object [Properties](properties-collection-ado.md) collection by the Data Shaping Service for OLE DB, or the connection string keyword "**Data Provider=***provider*".

No data provider is required if the **Recordset** is not populated (for example, as in a fabricated **Recordset** where columns are created with the NEW keyword). In that case, specify "**Data Provider=**none;".

## Example

``` 
 
Dim cnn As New ADODB.Connection 
cnn.Provider = "MSDataShape" 
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind" 
```

