---
title: "Recordset2 Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6ef57191-9da4-7904-d55c-60b59b895a50
description: "A Recordset2 object represents the records in a base table or the records that result from running a query."
---

# Recordset2 Members (DAO)

A **Recordset2** object represents the records in a base table or the records that result from running a query. 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[AddNew](recordset2-addnew-method-dao.md)** <br/> |Creates a new record for an updatable **Recordset2** object.  <br/> |
|**[Cancel](recordset2-cancel-method-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Cancels execution of a pending asynchronous method call (ODBCDirect workspaces only).  <br/> |
|**[CancelUpdate](recordset2-cancelupdate-method-dao.md)** <br/> |Cancels any pending updates for a **[Recordset](recordset-object-dao.md)** object.  <br/> |
|**[Clone](recordset2-clone-method-dao.md)** <br/> |Creates a duplicate **[Recordset](recordset-object-dao.md)** object that refers to the original **Recordset2** object.  <br/> |
|**[Close](recordset2-close-method-dao.md)** <br/> |Closes an open **Recordset**.  <br/> |
|**[CopyQueryDef](recordset2-copyquerydef-method-dao.md)** <br/> |Returns a **[QueryDef](querydef-object-dao.md)** object that is a copy of the **QueryDef** used to create the **[Recordset](recordset-object-dao.md)** object represented by the  _recordset_ placeholder (Microsoft Access workspaces only). .  <br/> |
|**[Delete](recordset2-delete-method-dao.md)** <br/> |Not supported for this object.  <br/> |
|**[Edit](recordset2-edit-method-dao.md)** <br/> |Copies the current record from an updatable **[Recordset](recordset-object-dao.md)** object to the copy buffer for subsequent editing.  <br/> |
|**[FillCache](recordset2-fillcache-method-dao.md)** <br/> |Fills all or a part of a local cache for a **Recordset** object that contains data from a Microsoft Access database engine-connected ODBC data source (Microsoft Access database engine-connected ODBC databases only).  <br/> |
|**[FindFirst](recordset2-findfirst-method-dao.md)** <br/> |Locates the first record in a dynaset- or snapshot-type **Recordset** object that satisfies the specified criteria and makes that record the current record (Microsoft Access workspaces only).  <br/> |
|**[FindLast](recordset2-findlast-method-dao.md)** <br/> |Locates the last record in a dynaset- or snapshot-type **[Recordset](recordset-object-dao.md)** object that satisfies the specified criteria and makes that record the current record (Microsoft Access workspaces only).  <br/> |
|**[FindNext](recordset2-findnext-method-dao.md)** <br/> |Locates the next record in a dynaset- or snapshot-type **[Recordset](recordset-object-dao.md)** object that satisfies the specified criteria and makes that record the current record (Microsoft Access workspaces only). .  <br/> |
|**[FindPrevious](recordset2-findprevious-method-dao.md)** <br/> |Locates the previous record in a dynaset- or snapshot-type **[Recordset](recordset-object-dao.md)** object that satisfies the specified criteria and makes that record the current record (Microsoft Access workspaces only). .  <br/> |
|**[GetRows](recordset2-getrows-method-dao.md)** <br/> |Retrieves multiple rows from a **[Recordset](recordset-object-dao.md)** object.  <br/> |
|**[Move](recordset2-move-method-dao.md)** <br/> |Moves the position of the current record in a **[Recordset](recordset-object-dao.md)** object.  <br/> |
|**[MoveFirst](recordset2-movefirst-method-dao.md)** <br/> |Moves to the first record in a specified **Recordset** object and make that record the current record.  <br/> |
|**[MoveLast](recordset2-movelast-method-dao.md)** <br/> |Moves to the last record in a specified **Recordset** object and make that record the current record.  <br/> |
|**[MoveNext](recordset2-movenext-method-dao.md)** <br/> |Moves to the next record in a specified **Recordset** object and make that record the current record.  <br/> |
|**[MovePrevious](recordset2-moveprevious-method-dao.md)** <br/> |Moves to the previous record in a specified **Recordset** object and make that record the current record.  <br/> |
|**[NextRecordset](recordset2-nextrecordset-method-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Gets the next set of records, if any, returned by a multi-part select query in an **[OpenRecordset](connection-openrecordset-method-dao.md)** call, and returns a **Boolean** value indicating whether one or more additional records are pending (ODBCDirect workspaces only).  <br/> |
|**[OpenRecordset](recordset2-openrecordset-method-dao.md)** <br/> |Creates a new **[Recordset](recordset-object-dao.md)** object and appends it to the **Recordsets** collection.  <br/> |
|**[Requery](recordset2-requery-method-dao.md)** <br/> |Updates the data in a **[Recordset](recordset-object-dao.md)** object by re-executing the query on which the object is based.  <br/> |
|**[Seek](recordset2-seek-method-dao.md)** <br/> |Locates the record in an indexed table-type **Recordset** object that satisfies the specified criteria for the current index and makes that record the current record (Microsoft Access workspaces only).  <br/> |
|**[Update](recordset2-update-method-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Saves the contents of the copy buffer to an updatable **[Recordset](recordset-object-dao.md)** object.  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[AbsolutePosition](recordset2-absoluteposition-property-dao.md)**|Sets or returns the relative record number of a **Recordset2** object's current record. |
|**[BatchCollisionCount](recordset2-batchcollisioncount-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns the number of records that did not complete the last batch update (ODBCDirect workspaces only).|
|**[BatchCollisions](recordset2-batchcollisions-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns an array of bookmarks indicating the rows that generated collisions in the last batch update operation (ODBCDirect workspaces only).|
|**[BatchSize](recordset2-batchsize-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Sets or returns the number of statements sent back to the server in each batch (ODBCDirect workspaces only).|
|**[BOF](recordset2-bof-property-dao.md)**|Returns a value that indicates whether the current record position is before the first record in a **Recordset** object. Read-only **Boolean**. |
|**[Bookmark](recordset2-bookmark-property-dao.md)**|Sets or returns a bookmark that uniquely identifies the current record in a **Recordset** object. |
|**[Bookmarkable](recordset2-bookmarkable-property-dao.md)**|Returns a value that indicates whether a **Recordset** object supports bookmarks, which you can set by using the **[Bookmark](recordset2-bookmark-property-dao.md)** property. |
|**[CacheSize](recordset2-cachesize-property-dao.md)**|Sets or returns the number of records retrieved from an ODBC data source that will be cached locally. Read/write **Long**. |
|**[CacheStart](recordset2-cachestart-property-dao.md)**|Sets or returns a value that specifies the bookmark of the first record in a dynaset-type Recordset object containing data to be locally cached from an ODBC data source (Microsoft Access workspaces only).|
|**[Connection](recordset2-connection-property-dao.md)**|Returns the **[Connection](connection-object-dao.md)** object that corresponds to the database. |
|**[DateCreated](recordset2-datecreated-property-dao.md)**|Returns the date and time a base table was created (Microsoft Access workspaces only). Read-only **Variant**. |
|**[EditMode](recordset2-editmode-property-dao.md)**|Returns a value that indicates the state of editing for the current record.|
|**[EOF](recordset2-eof-property-dao.md)**|Returns a value that indicates whether the current record position is after the last record in a **Recordset** object. Read-only **Boolean**. |
|**[Fields](recordset2-fields-property-dao.md)**|Returns a **Fields** collection that represents all stored **Field** objects for the specified object. Read-only. |
|**[Filter](recordset2-filter-property-dao.md)**|Sets or returns a value that determines the records included in a subsequently opened **Recordset** object (Microsoft Access workspaces only). Read/write **String**. |
|**[Index](recordset2-index-property-dao.md)**|Sets or returns a value that indicates the name of the current **[Index](index-object-dao.md)** object in a table-type **[Recordset](recordset-object-dao.md)** object (Microsoft Access workspaces only). |
|**[LastModified](recordset2-lastmodified-property-dao.md)**|Returns a ookmark indicating the most recently added or changed record.|
|**[LastUpdated](recordset2-lastupdated-property-dao.md)**| Returns the date and time of the most recent change made to a base table. Read-only **Variant**. |
|**[LockEdits](recordset2-lockedits-property-dao.md)**|Sets or returns a value indicating the type of locking that is in effect while editing.|
|**[Name](recordset2-name-property-dao.md)**|Returns the name of the specified object. Read-only **String**. |
|**[NoMatch](recordset2-nomatch-property-dao.md)**|Indicates whether a particular record was found by using the **[Seek](recordset2-seek-method-dao.md)** method or one of the **[Find](recordset2-findfirst-method-dao.md)** methods (Microsoft Access workspaces only). |
|**[ParentRecordset](recordset2-parentrecordset-property-dao.md)**|Returns the parent **Recordset** of the specified recordset. Read-only. |
|**[PercentPosition](recordset2-percentposition-property-dao.md)**|Sets or returns a value indicating the approximate location of the current record in the **[Recordset](recordset-object-dao.md)** object based on a percentage of the records in the **Recordset**. |
|**[Properties](recordset2-properties-property-dao.md)**|Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only. |
|**[RecordCount](recordset2-recordcount-property-dao.md)**|Returns the number of records accessed in a **[Recordset](recordset-object-dao.md)** object, or the total number of records in a table-type **Recordset** object. or **[TableDef](tabledef-object-dao.md)** object. Read-only **Long**. |
|**[RecordStatus](recordset2-recordstatus-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns a value indicating the update status of the current record if it is part of a batch update (ODBCDirect workspaces only). Read-only **[RecordStatusEnum](recordstatusenum-enumeration-dao.md)**. |
|**[Restartable](recordset2-restartable-property-dao.md)**|Returns a value that indicates whether a **[Recordset](recordset-object-dao.md)** object supports the **[Requery](recordset2-requery-method-dao.md)** method, which re-executes the query on which the **Recordset** object is based. |
|**[Sort](recordset2-sort-property-dao.md)**|Sets or returns the sort order for records in a **[Recordset](recordset-object-dao.md)** object (Microsoft Access workspaces only). |
|**[StillExecuting](recordset2-stillexecuting-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013 . Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Indicates whether or not an asynchronous operation (that is, a method called with the **dbRunAsync** option) has finished executing (ODBCDirect workspaces only). |
|**[Transactions](recordset2-transactions-property-dao.md)**|Returns a value that indicates whether an object supports transactions. Read-only **Boolean**. |
|**[Type](recordset2-type-property-dao.md)**|Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**. |
|**[Updatable](recordset2-updatable-property-dao.md)**|Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**. |
|**[UpdateOptions](recordset2-updateoptions-property-dao.md)**|
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Sets or returns a value that indicates how the WHERE clause is constructed for each record during a batch update, and whether the batch update should use an UPDATE statement or a DELETE followed by an INSERT (ODBCDirect workspaces only). Read/write **[UpdateCriteriaEnum](updatecriteriaenum-enumeration-dao.md)**. |
|**[ValidationRule](recordset2-validationrule-property-dao.md)**|Sets or returns a value that validates the data in a field as it's changed or added to a table (Microsoft Access workspaces only).Read/write **String**. |
|**[ValidationText](recordset2-validationtext-property-dao.md)**|Sets or returns a value that specifies the text of the message that your application displays if the value of a **Field** object doesn't satisfy the validation rule specified by the **ValidationRule** property setting (Microsoft Access workspaces only). Read-only **String**. |
   

