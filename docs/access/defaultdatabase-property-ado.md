---
title: "DefaultDatabase Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: a35c5631-f9d9-e51f-950b-e52169830d94
---

# DefaultDatabase Property (ADO)

Indicates the default database for a [Connection](connection-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns a **String** value that evaluates to the name of a database available from the provider. 
  
## Remarks

Use the **DefaultDatabase** property to set or return the name of the default database on a specific **Connection** object. 
  
If there is a default database, SQL strings may use an unqualified syntax to access objects in that database. To access objects in a database other than the one specified in the **DefaultDatabase** property, you must qualify object names with the desired database name. Upon connection, the provider will write default database information to the **DefaultDatabase** property. Some providers allow only one database per connection, in which case you cannot change the **DefaultDatabase** property. 
  
Some data sources and providers may not support this feature, and may return an error or an empty string.
  
 **Remote Data Service Usage** This property is not available on a client-side **Connection** object. 
  

