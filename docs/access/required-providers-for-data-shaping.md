---
title: "Required Providers for Data Shaping"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: eb8933fb-d533-3ea7-e045-35c1ca585765
description: "Data shaping typically requires two providers. The service provider, Data Shaping Service for OLE DB, supplies the data shaping functionality, and a data provider, such as the OLE DB Provider for SQL Server, supplies rows of data to populate the shaped Recordset."
---

# Required Providers for Data Shaping

Data shaping typically requires two providers. The service provider, [Data Shaping Service for OLE DB](microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), supplies the data shaping functionality, and a data provider, such as the OLE DB Provider for SQL Server, supplies rows of data to populate the shaped [Recordset](recordset-object-ado.md).
  
The name of the service provider (MSDataShape) can be specified as the value of the [Connection](connection-object-ado.md) object [Provider](provider-property-ado.md) property or the connection string keyword "Provider=MSDataShape;". 
  
The name of the data provider can be specified as the value of the **Data Provider** dynamic property, which is added to the **Connection** object [Properties](properties-collection-ado.md) collection by the Data Shaping Service for OLE DB, or the connection string keyword " **Data Provider=** *provider*  ". 
  
No data provider is required if the **Recordset** is not populated (for example, as in a fabricated **Recordset** where columns are created with the NEW keyword). In that case, specify " **Data Provider=** none;". 
  
## Example

```
 
Dim cnn As New ADODB.Connection 
cnn.Provider = "MSDataShape" 
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind" 

```


