---
title: "Workspace Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 13ac7d41-1b25-20d2-5c85-0f21bfd38328
description: "A Workspace object defines a named session for a user. It contains open databases and provides mechanisms for simultaneous transactions and, in Microsoft Access workspaces, secure workgroup support."
---

# Workspace Members (DAO)

A **Workspace** object defines a named session for a user. It contains open databases and provides mechanisms for simultaneous transactions and, in Microsoft Access workspaces, secure workgroup support. 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[BeginTrans](workspace-begintrans-method-dao.md)** <br/> |Begins a new transaction. Read/write **Database**.  <br/> |
|**[Close](workspace-close-method-dao.md)** <br/> |Closes an open **Workspace**.  <br/> |
|**[CommitTrans](workspace-committrans-method-dao.md)** <br/> |Ends the current transaction and saves the changes.  <br/> |
|**[CreateDatabase](workspace-createdatabase-method-dao.md)** <br/> |Creates a new **[Database](database-object-dao.md)** object, saves the database to disk, and returns an opened **Database** object (Microsoft Access workspaces only).  <br/> |
|**[OpenConnection](workspace-openconnection-method-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Opens a **[Connection](connection-object-dao.md)** object on an ODBC data source (ODBCDirect workspaces only).  <br/> |
|**[OpenDatabase](workspace-opendatabase-method-dao.md)** <br/> |Opens a specified database in a **[Workspace](workspace-object-dao.md)** object and returns a reference to the **[Database](database-object-dao.md)** object that represents it.  <br/> |
|**[Rollback](workspace-rollback-method-dao.md)** <br/> |Ends the current transaction and restores the databases in the **Workspace** object to the state they were in when the current transaction began.  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[Connections](workspace-connections-property-dao.md)**|Returns a **Connections** collection that represents the current connections in the specified **Workspace**. Read-only. |
|**[Databases](workspace-databases-property-dao.md)**|Returns a **Databases** collection that represents the open databases in the specified **Workspace**. Read-only. |
|**[DefaultCursorDriver](workspace-defaultcursordriver-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Sets or returns the type of cursor driver used on the connection created by the **[OpenConnection](dbengine-openconnection-method-dao.md)** or **[OpenDatabase](dbengine-opendatabase-method-dao.md)** methods (ODBCDirect workspaces only). |
|**[IsolateODBCTrans](workspace-isolateodbctrans-property-dao.md)**|Sets or returns a value that indicates whether multiple transactiond that involve the same Microsoft Access database engine-connected ODBC data source are isolated (Microsoft Access workspaces only).|
|**[LoginTimeout](workspace-logintimeout-property-dao.md)**|Sets or returns the number of seconds before an error occurs when you attempt to log on to an ODBC database.|
|**[Name](workspace-name-property-dao.md)**|Returns or sets the name of the specified object. Read/write **String** if the object has not been appended to a collection. Read-only **String** if the object has been appended to a collection. |
|**[Properties](workspace-properties-property-dao.md)**|Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only. |
|**[Type](workspace-type-property-dao.md)**|Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**. |
   

