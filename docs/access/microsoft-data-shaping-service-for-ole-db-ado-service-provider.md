---
title: "Microsoft Data Shaping Service for OLE DB (ADO Service Provider)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 6e6e5f39-6f43-7c7b-5812-796096d1d31b
description: "The Microsoft Data Shaping Service for OLE DB service provider supports the construction of hierarchical (shaped) Recordset objects from a data provider."
---

# Microsoft Data Shaping Service for OLE DB (ADO Service Provider)

The Microsoft Data Shaping Service for OLE DB service provider supports the construction of hierarchical (shaped) [Recordset](recordset-object-ado.md) objects from a data provider. 
  
## Provider Keyword

To invoke the Data Shaping Service for OLE DB, specify the following keyword and value in the connection string.
  
```
 
"Provider=MSDataShape" 

```

## Dynamic Properties

When this service provider is invoked, the following dynamic properties are added to the [Connection](connection-object-ado.md) object's [Properties](properties-collection-ado.md) collection. 
  
|**Dynamic Property Name**|**Description**|
|:-----|:-----|
|**Unique Reshape Names** <br/> |Indicates whether **Recordset** objects with duplicate values for their **Reshape Name** properties are allowed. If this dynamic property is **True** and a new **Recordset** is created with the same user-specified reshape name as an existing **Recordset**, then the new **Recordset** object's reshape name is modified to make it unique. If this property is **False** and a new **Recordset** is created with the same user-specified reshape name as the existing **Recordset**, both **Recordset** objects will have the same reshape name. Therefore, neither **Recordset** can be reshaped as long as both recordsets exist. The default value of the property is **False**.  <br/> |
|**Data Provider** <br/> |Indicates the name of the provider that will supply rows to be shaped. This value may be NONE if a provider will not be used to supply rows.  <br/> |
   
You may also set writable dynamic properties by specifying their names as keywords in the connection string. For example, in Microsoft Visual Basic, set the **Data Provider** dynamic property to "MSDASQL" by specifying: 
  
```
 
Dim cn as New ADODB.Connection 
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL" 

```

You may also set or retrieve a dynamic property by specifying its name as the index to the [Properties](properties-collection-ado.md) property. For example, get and print the current value of the **Data Provider** dynamic property, then set a new value, like this: 
  
```
 
Debug.Print cn.Properties("Data Provider") 
cn.Properties("Data Provider") = "MSDASQL" 

```

For more information about data shaping, see [Data Shaping](data-shaping-summary.md).
  

