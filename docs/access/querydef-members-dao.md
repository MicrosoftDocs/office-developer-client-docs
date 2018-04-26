---
title: "QueryDef Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 3f914d23-aa63-3ebd-1d86-4f53da71131b
description: "A QueryDef object is a stored definition of a query in a Microsoft Access database engine database."
---

# QueryDef Members (DAO)

A **QueryDef** object is a stored definition of a query in a Microsoft Access database engine database. 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[Cancel](querydef-cancel-method-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Cancels execution of a pending asynchronous method call (ODBCDirect workspaces only).  <br/> |
|**[Close](querydef-close-method-dao.md)** <br/> |Closes an open **QueryDef**.  <br/> |
|**[CreateProperty](querydef-createproperty-method-dao.md)** <br/> |Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
|**[Execute](querydef-execute-method-dao.md)** <br/> |Executes an SQL statement on the specified object.  <br/> |
|**[OpenRecordset](querydef-openrecordset-method-dao.md)** <br/> |Creates a new **[Recordset](recordset-object-dao.md)** object and appends it to the **Recordsets** collection.  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[CacheSize](querydef-cachesize-property-dao.md)**|Sets or returns the number of records retrieved from an ODBC data source that will be cached locally. Read/write **Long**. |
|**[Connect](querydef-connect-property-dao.md)**|Sets or returns a value that provides information about the source of database used in a pass-through query. Read-only **String**. |
|**[DateCreated](querydef-datecreated-property-dao.md)**|Returns the date and time that an object was created (Microsoft Access workspaces only). Read-only **Variant**. |
|**[Fields](querydef-fields-property-dao.md)**|Returns a **[Fields](fields-collection-dao.md)** collection that represents all stored **[Field](field-object-dao.md)** objects for the specified object. Read-only. |
|**[LastUpdated](querydef-lastupdated-property-dao.md)**|Returns the date and time of the most recent change made to an object. Read-only **Variant**. |
|**[MaxRecords](querydef-maxrecords-property-dao.md)**|Sets or returns the maximum number of records to return from a query against an ODBC data source.|
|**[Name](querydef-name-property-dao.md)**|Returns or sets the name of the specified object. Read/write **String**. |
|**[ODBCTimeout](querydef-odbctimeout-property-dao.md)**|Indicates the number of seconds to wait before a timeout error occurs when a **[QueryDef](querydef-object-dao.md)** is executed on an ODBC database. |
|**[Parameters](querydef-parameters-property-dao.md)**|Returns a **[Parameters](parameters-collection-dao.md)** collection that contains all of the **[Parameter](parameter-object-dao.md)** objects of the specified **QueryDef**. Read-only. |
|**[Prepare](querydef-prepare-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Sets or returns a value that indicates whether the query should be prepared on the server as a temporary stored procedure, using the ODBC **SQLPrepare** API function, prior to execution, or just executed using the ODBC **SQLExecDirect** API function (ODBCDirect workspaces only). Read/Write **[QueryDefStateEnum](querydefstateenum-enumeration-dao.md)**. |
|**[Properties](querydef-properties-property-dao.md)**|Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only. |
|**[RecordsAffected](querydef-recordsaffected-property-dao.md)**|Returns the number of records affected by the most recently invoked **[Execute](querydef-execute-method-dao.md)** method. |
|**[ReturnsRecords](querydef-returnsrecords-property-dao.md)**|Sets or returns a value that indicates whether an SQL pass-through query to an external database returns records (Microsoft Access workspaces only).|
|**[SQL](querydef-sql-property-dao.md)**|Sets or returns the SQL statement that defines the query executed by a **[QueryDef](querydef-object-dao.md)** object. |
|**[StillExecuting](querydef-stillexecuting-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Indicates whether or not an asynchronous operation (that is, a method called with the [dbRunAsync](recordsetoptionenum-enumeration-dao.md) option) has finished executing (ODBCDirect workspaces only). |
|**[Type](querydef-type-property-dao.md)**|Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**. |
|**[Updatable](querydef-updatable-property-dao.md)**|Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**. |
   

