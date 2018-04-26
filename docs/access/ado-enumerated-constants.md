---
title: "ADO Enumerated Constants"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 7c983acd-8b38-dc3c-6704-46e649ebb7d6
description: "To assist in debugging, the ADO enumerations list a value for each constant. However, this value is purely advisory, and may change from one release of ADO to another. Your code should only depend on the name, not the actual value, of each enumerated constant."
---

# ADO Enumerated Constants

To assist in debugging, the ADO enumerations list a value for each constant. However, this value is purely advisory, and may change from one release of ADO to another. Your code should only depend on the name, not the actual value, of each enumerated constant.
  
|||
|:-----|:-----|
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](adcprop_asyncthreadpriority_enum.md) <br/> |For an RDS **Recordset** object, specifies the execution priority of the asynchronous thread that retrieves data.  <br/> |
|[ADCPROP_AUTORECALC_ENUM](adcprop_autorecalc_enum.md) <br/> |Specifies when the **MSDataShape** provider re-calculates aggregate and calculated columns in a hierarchical **Recordset**.  <br/> |
|[ADCPROP_UPDATECRITERIA_ENUM](adcprop_updatecriteria_enum.md) <br/> |Specifies which fields can be used to detect conflicts during an optimistic update of a row of the data source with a **Recordset** object.  <br/> |
|[ADCPROP_UPDATERESYNC_ENUM](adcprop_updateresync_enum.md) <br/> |Specifies whether the **UpdateBatch** method is followed by an implicit **Resync** method operation and if so, the scope of that operation.  <br/> |
|[AffectEnum](affectenum.md) <br/> |Specifies which records are affected by an operation.  <br/> |
|[BookmarkEnum](bookmarkenum.md) <br/> |Specifies a bookmark indicating where the operation should begin.  <br/> |
|[CommandTypeEnum](commandtypeenum.md) <br/> |Specifies how a command argument should be interpreted.  <br/> |
|[CompareEnum](compareenum.md) <br/> |Specifies the relative position of two records represented by their bookmarks.  <br/> |
|[ConnectModeEnum](connectmodeenum.md) <br/> |Specifies the available permissions for modifying data in a **Connection**, opening a **Record**, or specifying values for the **Mode** property of the **Record** and **Stream** objects.  <br/> |
|[ConnectOptionEnum](connectoptionenum.md) <br/> |Specifies whether the **Open** method of a **Connection** object should return after (synchronously) or before (asynchronously) the connection is established.  <br/> |
|[ConnectPromptEnum](connectpromptenum.md) <br/> |Specifies whether a dialog box should be displayed to prompt for missing parameters when opening a connection to an ODBC data source.  <br/> |
|[CopyRecordOptionsEnum](copyrecordoptionsenum.md) <br/> |Specifies the behavior of the **CopyRecord** method.  <br/> |
|[CursorLocationEnum](cursorlocationenum.md) <br/> |Specifies the location of the cursor engine.  <br/> |
|[CursorOptionEnum](cursoroptionenum.md) <br/> |Specifies what functionality the **Supports** method should test for.  <br/> |
|[CursorTypeEnum](cursortypeenum.md) <br/> |Specifies the type of cursor used in a **Recordset** object.  <br/> |
|[DataTypeEnum](datatypeenum.md) <br/> |Specifies the data type of a **Field**, **Parameter**, or **Property**.  <br/> |
|[EditModeEnum](editmodeenum.md) <br/> |Specifies the editing status of a record.  <br/> |
|[ErrorValueEnum](errorvalueenum.md) <br/> |Specifies the type of ADO run-time error.  <br/> |
|[EventReasonEnum](eventreasonenum.md) <br/> |Specifies the reason that caused an event to occur.  <br/> |
|[EventStatusEnum](eventstatusenum.md) <br/> |Specifies the current status of the execution of an event.  <br/> |
|[ExecuteOptionEnum](executeoptionenum.md) <br/> |Specifies how a provider should execute a command.  <br/> |
|[FieldEnum](fieldenum.md) <br/> |Specifies the special fields referenced in a **Record** object's **Fields** collection.  <br/> |
|[FieldAttributeEnum](fieldattributeenum.md) <br/> |Specifies one or more attributes of a **Field** object.  <br/> |
|[FieldStatusEnum](fieldstatusenum.md) <br/> |Specifies the status of a **Field** object.  <br/> |
|[FilterGroupEnum](filtergroupenum.md) <br/> |Specifies the group of records to be filtered from a **Recordset**.  <br/> |
|[GetRowsOptionEnum](getrowsoptionenum.md) <br/> |Specifies how many records to retrieve from a **Recordset**.  <br/> |
|[IsolationLevelEnum](isolationlevelenum.md) <br/> |Specifies the level of transaction isolation for a **Connection** object.  <br/> |
|[LineSeparatorsEnum](lineseparatorsenum.md) <br/> |Specifies the character used as a line separator in text **Stream** objects.  <br/> |
|[LockTypeEnum](locktypeenum.md) <br/> |Specifies the type of lock placed on records during editing.  <br/> |
|[MarshalOptionsEnum](marshaloptionsenum.md) <br/> |Specifies which records should be returned to the server.  <br/> |
|[MoveRecordOptionsEnum](moverecordoptionsenum.md) <br/> |Specifies the behavior of the **Record** object **MoveRecord** method.  <br/> |
|[ObjectStateEnum](objectstateenum.md) <br/> |Specifies whether an object is open or closed, connecting to a data source, executing a command, or fetching data.  <br/> |
|[ParameterAttributesEnum](parameterattributesenum.md) <br/> |Specifies the attributes of a **Parameter** object.  <br/> |
|[ParameterDirectionEnum](parameterdirectionenum.md) <br/> |Specifies whether the **Parameter** represents an input parameter, an output parameter, or both, or if the parameter is the return value from a stored procedure.  <br/> |
|[PersistFormatEnum](persistformatenum.md) <br/> |Specifies the format in which to save a **Recordset**.  <br/> |
|[PositionEnum](positionenum.md) <br/> |Specifies the current position of the record pointer within a **Recordset**.  <br/> |
|[PropertyAttributesEnum](propertyattributesenum.md) <br/> |Specifies the attributes of a **Property** object.  <br/> |
|[RecordCreateOptionsEnum](recordcreateoptionsenum.md) <br/> |Specifies for the **Record** object **Open** method whether an existing **Record** should be opened, or a new **Record** should be created.  <br/> |
|[RecordOpenOptionsEnum](recordopenoptionsenum.md) <br/> |Specifies options for opening a **Record**. These values may be combined by using an OR operator.  <br/> |
|[RecordStatusEnum](recordstatusenum.md) <br/> |Specifies the status of a record with regard to batch updates and other bulk operations.  <br/> |
|[RecordTypeEnum](recordtypeenum.md) <br/> |Specifies the type of **Record** object.  <br/> |
|[ResyncEnum](resyncenum.md) <br/> |Specifies whether underlying values are overwritten by a call to **Resync**.  <br/> |
|[SaveOptionsEnum](saveoptionsenum.md) <br/> |Specifies whether a file should be created or overwritten when saving from a **Stream** object. The values can be combined with an AND operator.  <br/> |
|[SchemaEnum](schemaenum.md) <br/> |Specifies the type of schema **Recordset** that the **OpenSchema** method retrieves. Specifies the direction of a record search within a **Recordset**.  <br/> |
|[SearchDirectionEnum](searchdirectionenum.md) <br/> |Specifies the direction of a record search within a **Recordset**.Specifies the type of **Seek** to execute.  <br/> |
|[SeekEnum](seekenum.md) <br/> |Specifies the type of **Seek** to execute.Specifies options for opening a **Stream** object. The values can be combined with an AND operator.  <br/> |
|[StreamOpenOptionsEnum](streamopenoptionsenum.md) <br/> |Specifies options for opening a **Stream** object. The values can be combined with an AND operator.Specifies whether the whole stream or the next line should be read from a **Stream** object.  <br/> |
|[StreamReadEnum](streamreadenum.md) <br/> |Specifies whether the whole stream or the next line should be read from a **Stream** object.Specifies the type of data stored in a **Stream** object.  <br/> |
|[StreamTypeEnum](streamtypeenum.md) <br/> |Specifies the type of data stored in a **Stream** object.Specifies whether a line separator is appended to the string written to a **Stream** object.  <br/> |
|[StreamWriteEnum](streamwriteenum.md) <br/> |Specifies whether a line separator is appended to the string written to a **Stream** object.Specifies the format when retrieving a **Recordset** as a string.  <br/> |
|[StringFormatEnum](stringformatenum.md) <br/> |Specifies the format when retrieving a **Recordset** as a string.Specifies the transaction attributes of a **Connection** object.  <br/> |
|[XactAttributeEnum](xactattributeenum.md) <br/> |Specifies the transaction attributes of a **Connection** object.  <br/> |
   

