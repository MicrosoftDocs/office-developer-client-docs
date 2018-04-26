---
title: "DBEngine Members (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 740b6a85-585f-0e1d-710b-84ba24825325
description: "The DBEngine object is the top level object in the DAO object model."
---

# DBEngine Members (DAO)

The **DBEngine** object is the top level object in the DAO object model. 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[BeginTrans](dbengine-begintrans-method-dao.md)** <br/> |Begins a new transaction. Read/write **Database**.  <br/> |
|**[CommitTrans](dbengine-committrans-method-dao.md)** <br/> |Ends the current transaction and saves the changes.  <br/> |
|**[CompactDatabase](dbengine-compactdatabase-method-dao.md)** <br/> |Copies and compacts a closed database, and gives you the option of changing its version, collating order, and encryption. (Microsoft Access workspaces only). .  <br/> |
|**[CreateDatabase](dbengine-createdatabase-method-dao.md)** <br/> |Creates a new **[Database](database-object-dao.md)** object, saves the database to disk, and returns an opened **Database** object (Microsoft Access workspaces only). .  <br/> |
|**[CreateWorkspace](dbengine-createworkspace-method-dao.md)** <br/> |Creates a new **[Workspace](workspace-object-dao.md)** object.  <br/> |
|**[Idle](dbengine-idle-method-dao.md)** <br/> |Suspends data processing, enabling the Microsoft Access database engine to complete any pending tasks, such as memory optimization or page timeouts (Microsoft Access workspaces only).  <br/> |
|**[OpenConnection](dbengine-openconnection-method-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Opens a **[Connection](connection-object-dao.md)** object on an ODBC data source (ODBCDirect workspaces only).  <br/> |
|**[OpenDatabase](dbengine-opendatabase-method-dao.md)** <br/> |Opens a specified database and returns a reference to the **[Database](database-object-dao.md)** object that represents it.  <br/> |
|**[RegisterDatabase](dbengine-registerdatabase-method-dao.md)** <br/> |Enters connection information for an ODBC data source in the Windows Registry. The ODBC driver needs connection information when the ODBC data source is opened during a session.  <br/> |
|**[Rollback](dbengine-rollback-method-dao.md)** <br/> |Ends the current transaction and restores the databases in the **Workspace** object to the state they were in when the current transaction began.  <br/> |
|**[SetOption](dbengine-setoption-method-dao.md)** <br/> |Temporarily overrides values for the Microsoft Access database engine keys in the Windows Registry (Microsoft Access workspaces only).  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[DefaultPassword](dbengine-defaultpassword-property-dao.md)** <br/> |Sets the password used to create the default **Workspace** when it is initialized. Read/write **String**.  <br/> |
|**[DefaultType](dbengine-defaulttype-property-dao.md)** <br/> |Sets or returns a value that indicates what type of workspace will be used by the next **[Workspace](workspace-object-dao.md)** object created.  <br/> |
|**[DefaultUser](dbengine-defaultuser-property-dao.md)** <br/> |Sets the user name used to create the default **Workspace** when it is initialized. Read/write **String**.  <br/> |
|**[Errors](dbengine-errors-property-dao.md)** <br/> |Returns an **Errors** collection that contains all of the stored **Error** objects for the specified object. Read-only.  <br/> |
|**[IniPath](dbengine-inipath-property-dao.md)** <br/> |Sets or returns information about the Windows Registry key that contains values for the Microsoft Access database engine (Microsoft Access workspaces only).  <br/> |
|**[LoginTimeout](dbengine-logintimeout-property-dao.md)** <br/> |Sets or returns the number of seconds before an error occurs when you attempt to log on to an ODBC database.  <br/> |
|**[Properties](dbengine-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[Version](dbengine-version-property-dao.md)** <br/> |Rreturns the version of DAO currently in use. Read-only **String**.  <br/> |
|**[Workspaces](dbengine-workspaces-property-dao.md)** <br/> |Returns a **Workspaces** collection that contains all of the active, unhidden **Workspace** objects. Read-only.  <br/> |
   

