---
title: "ADO Methods"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 1fd965a0-711c-e199-822c-b9575c5034bd
description: ""
---

# ADO Methods

|||
|:-----|:-----|
|[AddNew](addnew-method-ado.md) <br/> |Creates a new record for an updatable **Recordset** object.  <br/> |
|[Append](append-method-ado.md) <br/> |Appends an object to a collection. If the collection is **Fields**, a new **Field** object may be created before it is appended to the collection.  <br/> |
|[AppendChunk](appendchunk-method-ado.md) <br/> |Appends data to a large text or binary data **Field**, or to a **Parameter** object.  <br/> |
|[BeginTrans, CommitTrans, and RollbackTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) <br/> |Manages transaction processing within a **Connection** object as follows: **BeginTrans** — Begins a new transaction.           **CommitTrans** — Saves any changes and ends the current transaction. It may also start a new transaction.           **RollbackTrans** — Cancels any changes and ends the current transaction. It may also start a new transaction.  <br/> |
|[Cancel](cancel-method-ado.md) <br/> |Cancels execution of a pending, asynchronous method call.  <br/> |
|[CancelBatch](cancelbatch-method-ado.md) <br/> |Cancels a pending batch update.  <br/> |
|[CancelUpdate](cancelupdate-method-ado.md) <br/> |Cancels any changes made to the current or new row of a **Recordset** object, or the **Fields** collection of a **Record** object, before calling the **Update** method.  <br/> |
|[Clear](clear-method-ado.md) <br/> |Removes all the **Error** objects from the **Errors** collection.  <br/> |
|[Clone](clone-method-ado.md) <br/> |Creates a duplicate **Recordset** object from an existing **Recordset** object. Optionally, specifies that the clone be read-only.  <br/> |
|[Close](close-method-ado.md) <br/> |Closes an open object and any dependent objects.  <br/> |
|[CompareBookmarks](comparebookmarks-method-ado.md) <br/> |Compares two bookmarks and returns an indication of their relative values.  <br/> |
|[CopyRecord](copyrecord-method-ado.md) <br/> |Copies a file or directory, and its contents, to another location.  <br/> |
|[CopyTo](copyto-method-ado.md) <br/> |Copies the specified number of characters or bytes (depending on **Type** ) in the **Stream** to another **Stream** object.  <br/> |
|[CreateParameter](createparameter-method-ado.md) <br/> |Creates a new **Parameter** object with the specified properties.  <br/> |
|[Delete (ADO Parameters Collection)](delete-method-ado-parameters-collection.md) <br/> |Deletes an object from the **Parameters** collection.  <br/> |
|[Delete (ADO Fields Collection)](delete-method-ado-fields-collection.md) <br/> |Deletes an object from the **Fields** collection.  <br/> |
|[Delete (ADO Recordset)](delete-method-ado-recordset.md) <br/> |Deletes the current record or a group of records.  <br/> |
|[DeleteRecord](deleterecord-method-ado.md) <br/> |Deletes a file or directory, and all its subdirectories.  <br/> |
|[Execute (ADO Command)](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx) <br/> |Executes the query, SQL statement, or stored procedure specified in the **CommandText** property.  <br/> |
|[Execute (ADO Connection)](http://msdn.microsoft.com/library/af190bd9-7167-df59-29ca-a9a86c4957fd%28Office.15%29.aspx) <br/> |Executes the specified query, SQL statement, stored procedure, or provider-specific text.  <br/> |
|[Find](find-method-ado.md) <br/> |Searches a **Recordset** for the row that satisfies the specified criteria.  <br/> |
|[Flush](flush-method-ado.md) <br/> |Forces the contents of the **Stream** remaining in the ADO buffer to the underlying object with which the **Stream** is associated.  <br/> |
|[GetChildren](getchildren-method-ado.md) <br/> |Returns a **Recordset** whose rows represent the files and subdirectories in the directory represented by this **Record**.  <br/> |
|[GetChunk](getchunk-method-ado.md) <br/> |Returns all, or a portion of, the contents of a large text or binary data **Field** object.  <br/> |
|[GetRows](getrows-method-ado.md) <br/> |Retrieves multiple records of a **Recordset** object into an array.  <br/> |
|[GetString](getstring-method-ado.md) <br/> |Returns the **Recordset** as a string.  <br/> |
|[LoadFromFile](loadfromfile-method-ado.md) <br/> |Loads the contents of an existing file into a **Stream**.  <br/> |
|[Move](move-method-ado.md) <br/> |Moves the position of the current record in a **Recordset** object.  <br/> |
|[MoveFirst, MoveLast, MoveNext, and MovePrevious](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Moves to the first, last, next, or previous record in a specified **Recordset** object and makes that record the current record.  <br/> |
|[MoveRecord](moverecord-method-ado.md) <br/> |Moves a file, or a directory and its contents, to another location.  <br/> |
|[NextRecordset](nextrecordset-method-ado.md) <br/> |Clears the current **Recordset** object and returns the next **Recordset** by advancing through a series of commands.  <br/> |
|[Open (ADO Connection)](open-method-ado-connection.md) <br/> |Opens a connection to a data source.  <br/> |
|[Open (ADO Record)](open-method-ado-record.md) <br/> |Opens an existing **Record** object, or creates a new file or directory.  <br/> |
|[Open (ADO Recordset)](open-method-ado-recordset.md) <br/> |Opens a cursor.  <br/> |
|[Open (ADO Stream)](open-method-ado-stream.md) <br/> |Opens a **Stream** object to manipulate streams of binary or text data.  <br/> |
|[OpenSchema](openschema-method-ado.md) <br/> |Obtains database schema information from the provider.  <br/> |
|[Read](read-method-ado.md) <br/> |Reads a specified number of bytes from a **Stream** object.  <br/> |
|[ReadText](readtext-method-ado.md) <br/> |Reads a specified number of characters from a text **Stream** object.  <br/> |
|[Refresh](refresh-method-ado.md) <br/> |Updates the objects in a collection to reflect objects available from, and specific to, the provider.  <br/> |
|[Requery](requery-method-ado.md) <br/> |Updates the data in a **Recordset** object by re-executing the query on which the object is based.  <br/> |
|[Resync](resync-method-ado.md) <br/> |Refreshes the data in the current **Recordset** object, or **Fields** collection of a **Record** object, from the underlying database.  <br/> |
|[Save](save-method-ado.md) <br/> |Saves the **Recordset** in a file or **Stream** object.  <br/> |
|[SaveToFile](savetofile-method-ado.md) <br/> |Saves the binary contents of a **Stream** to a file.  <br/> |
|[Seek](seek-method-ado.md) <br/> |Searches the index of a **Recordset** to quickly locate the row that matches the specified values, and changes the current row position to that row.  <br/> |
|[SetEOS](seteos-method-ado.md) <br/> |Sets the position that is the end of the stream.  <br/> |
|[SkipLine](skipline-method-ado.md) <br/> |Skips one entire line when reading a text stream.  <br/> |
|[Stat](stat-method-ado.md) <br/> |Gets statistical information about an open stream.  <br/> |
|[Supports](supports-method-ado.md) <br/> |Determines whether a specified **Recordset** object supports a particular type of functionality.  <br/> |
|[Update](update-method-ado.md) <br/> |Saves any changes you make to the current row of a **Recordset** object, or the **Fields** collection of a **Record** object.  <br/> |
|[UpdateBatch](updatebatch-method-ado.md) <br/> |Writes all pending batch updates to disk.  <br/> |
|[Write](write-method-ado.md) <br/> |Writes binary data to a **Stream** object.  <br/> |
|[WriteText](writetext-method-ado.md) <br/> |Writes a specified text string to a **Stream** object.  <br/> |
   

