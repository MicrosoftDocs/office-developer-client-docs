---
title: "Connection Members (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 94fc60ee-b6f2-cf08-b008-ed51bf7e7f8c
description: ""
---

# Connection Members (DAO)

> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine.A **Connection** object represents a connection to an ODBC database (ODBCDirect workspaces only). 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[Cancel](connection-cancel-method-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Cancels execution of a pending asynchronous method call (ODBCDirect workspaces only).  <br/> |
|**[Close](connection-close-method-dao.md)** <br/> |Closes an open **Connection**.  <br/> |
|**[CreateQueryDef](connection-createquerydef-method-dao.md)** <br/> |Creates a new **[QueryDef](querydef-object-dao.md)** object.  <br/> |
|**[Execute](connection-execute-method-dao.md)** <br/> |Runs an action query or executes an SQL statement on the specified object.  <br/> |
|**[OpenRecordset](connection-openrecordset-method-dao.md)** <br/> |Creates a new **[Recordset](recordset-object-dao.md)** object and appends it to the **Recordsets** collection.  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[Connect](connection-connect-property-dao.md)**|Sets or returns a value that provides information about the source of an open connection. Read/write **String**. |
|**[Database](connection-database-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns the **[Database](database-object-dao.md)** object that corresponds to this connection (ODBCDirect workspaces only). |
|**[Name](connection-name-property-dao.md)**|Rreturns the name of a **[Connection](connection-object-dao.md)**. |
|**[QueryDefs](connection-querydefs-property-dao.md)**|Returns a **QueryDefs** collection that contains all of the **QueryDef** objects of the specified connection. Read-only. |
|**[QueryTimeout](connection-querytimeout-property-dao.md)**|Sets or returns a value that specifies the number of seconds to wait before a timeout error occurs when a query is executed on an ODBC data source.|
|**[RecordsAffected](connection-recordsaffected-property-dao.md)**|Returns the number of records affected by the most recently invoked **[Execute](connection-execute-method-dao.md)** method. |
|**[Recordsets](connection-recordsets-property-dao.md)**|Returns a **Recordsets** collection that contains all of the open recordsets in the for the specified connection. Read-only. |
|**[StillExecuting](connection-stillexecuting-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Indicates whether or not an asynchronous operation (that is, a method called with the **dbRunAsync** option) has finished executing (ODBCDirect workspaces only). |
|**[Transactions](connection-transactions-property-dao.md)**|Returns a value that indicates whether an object supports transactions. Read-only **Boolean**. |
|**[Updatable](connection-updatable-property-dao.md)**|Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**.Read-only. |
   

