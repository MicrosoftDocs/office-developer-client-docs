---
title: "Connection.QueryTimeout Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052905
  
localization_priority: Normal
ms.assetid: 97853412-d5ae-7a71-ccaa-595c68919654
description: "Sets or returns a value that specifies the number of seconds to wait before a timeout error occurs when a query is executed on an ODBC data source."
---

# Connection.QueryTimeout Property (DAO)

Sets or returns a value that specifies the number of seconds to wait before a timeout error occurs when a query is executed on an ODBC data source.
  
## Syntax

 *expression*  . **QueryTimeout**
  
 *expression*  A variable that represents a **Connection** object. 
  
## Remarks

The default value is 60.
  
When you're using an ODBC database, such as Microsoft SQL Server, there may be delays due to network traffic or heavy use of the ODBC server. Rather than waiting indefinitely, you can specify how long to wait.
  
When you use **QueryTimeout** with a **[Connection](connection-object-dao.md)** or **[Database](database-object-dao.md)** object, it specifies a global value for all queries associated with the database. You can override this value for a specific query by setting the **ODBCTimeout** property of the particular **[QueryDef](querydef-object-dao.md)** object. 
  

