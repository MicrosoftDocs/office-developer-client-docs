---
title: "Database Members (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 68b0c069-8ed9-64dc-ea68-0d323e24c79c
description: "A Database object represents an open database."
---

# Database Members (DAO)

A **Database** object represents an open database. 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[Close](database-close-method-dao.md)** <br/> |Closes an open **Database**.  <br/> |
|**[CreateProperty](database-createproperty-method-dao.md)** <br/> |Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only). .  <br/> |
|**[CreateQueryDef](database-createquerydef-method-dao.md)** <br/> |Creates a new **[QueryDef](querydef-object-dao.md)** object.  <br/> |
|**[CreateRelation](database-createrelation-method-dao.md)** <br/> |Creates a new **[Relation](relation-object-dao.md)** object (Microsoft Access workspaces only). .  <br/> |
|**[CreateTableDef](database-createtabledef-method-dao.md)** <br/> |Creates a new **[TableDef](tabledef-object-dao.md)** object (Microsoft Access workspaces only). .  <br/> |
|**[Execute](database-execute-method-dao.md)** <br/> |Runs an action query or executes an SQL statement on the specified object.  <br/> |
|**[MakeReplica](database-makereplica-method-dao.md)** <br/> |Makes a new replica from another database replica (Microsoft Access workspaces only).  <br/> |
|**[NewPassword](database-newpassword-method-dao.md)** <br/> |Changes the password of an existing Microsoft Access database engine database (Microsoft Access workspaces only).  <br/> |
|**[OpenRecordset](database-openrecordset-method-dao.md)** <br/> |Creates a new **[Recordset](recordset-object-dao.md)** object and appends it to the **Recordsets** collection.  <br/> |
|**[PopulatePartial](database-populatepartial-method-dao.md)** <br/> |Synchronizes any changes in a partial replica with the full replica, clears all records in the partial replica, and then repopulates the partial replica based on the current replica filters. (Microsoft Access database engine databases only.).  <br/> |
|**[Synchronize](database-synchronize-method-dao.md)** <br/> |Synchronizes two replicas. (Microsoft Access workspaces only).  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[CollatingOrder](database-collatingorder-property-dao.md)** <br/> |Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only **Long**.  <br/> |
|**[Connect](database-connect-property-dao.md)** <br/> |Sets or returns a value that provides information about the source an open database. Read/write **String**.  <br/> |
|**[Connection](database-connection-property-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns the **[Connection](connection-object-dao.md)** object that corresponds to the database (ODBCDirect workspaces only).  <br/> |
|**[Containers](database-containers-property-dao.md)** <br/> |Returns a **Containers** collection that represents all of the **Container** objects in the specifed database. Read-only.  <br/> |
|**[DesignMasterID](database-designmasterid-property-dao.md)** <br/> |Sets or returns a 16-byte value that uniquely identifies the Design Master in a replica set (Microsoft Access workspaces only).  <br/> |
|**[Name](database-name-property-dao.md)** <br/> |Returns the name of the specified object. Read-only **String**.  <br/> |
|**[Properties](database-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[QueryDefs](database-querydefs-property-dao.md)** <br/> |Returns a **QueryDefs** collection that contains all of the **QueryDef** objects of the specified database. Read-only.  <br/> |
|**[QueryTimeout](database-querytimeout-property-dao.md)** <br/> |Sets or returns a value that specifies the number of seconds to wait before a timeout error occurs when a query is executed on an ODBC data source.  <br/> |
|**[RecordsAffected](database-recordsaffected-property-dao.md)** <br/> |Returns the number of records affected by the most recently invoked **[Execute](connection-execute-method-dao.md)** method.  <br/> |
|**[Recordsets](database-recordsets-property-dao.md)** <br/> |Returns a **Recordsets** collection that contains all of the open recordsets in the for the specified database. Read-only.  <br/> |
|**[Relations](database-relations-property-dao.md)** <br/> |Returns a **Relations** collection that contains all of the stored **Relation** objects for the specified database. Read-only.  <br/> |
|**[ReplicaID](database-replicaid-property-dao.md)** <br/> |Returns a 16-byte value that uniquely identifies a database replica (Microsoft Access workspaces only).  <br/> |
|**[TableDefs](database-tabledefs-property-dao.md)** <br/> |Returns a **TableDefs** collection that contains all of the **TableDef** objects stored in the specified database. Read-only.  <br/> |
|**[Transactions](database-transactions-property-dao.md)** <br/> |Returns a value that indicates whether an object supports transactions. Read-only **Boolean**.  <br/> |
|**[Updatable](database-updatable-property-dao.md)** <br/> |Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**.  <br/> |
|**[Version](database-version-property-dao.md)** <br/> |In a Microsoft Access workspace, returns the vesion of the Microsoft Jet or Microsoft Access database engine that created the database. Read-only **String**.  <br/> |
   

