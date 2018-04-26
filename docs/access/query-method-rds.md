---
title: "Query Method (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c88d82bd-2139-7f1e-4e5e-9030f3795816

---

# Query Method (RDS)

Uses a valid SQL query string to return a [Recordset](recordset-object-ado.md).
  
## Syntax

 **Set** *Recordset*  =  *DataFactory*  . **Query**( *Connection*  ,  *Query*  ) 
  
## Parameters

-  *Recordset* 
    
- An object variable that represents a **Recordset** object. 
    
-  *DataFactory* 
    
- An object variable that represents an [RDSServer.DataFactory](datafactory-object-rdsserver.md) object. 
    
-  *Connection* 
    
- A **String** value that contains the server connection information. This is similar to the [Connect](connect-property-rds.md) property. 
    
-  *Query* 
    
- A **String** that contains the SQL query. 
    
## Remarks

The query should use the SQL dialect of the database server. A result status is returned if there is an error with the query that was executed. The **Query** method doesn't perform any syntax checking on the **Query** string. 
  

