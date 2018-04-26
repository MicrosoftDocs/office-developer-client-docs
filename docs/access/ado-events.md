---
title: "ADO Events"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 84ca9525-99cb-4ba6-2a4d-172414b8f0cc
description: ""
---

# ADO Events

|||
|:-----|:-----|
|[BeginTransComplete](begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md) <br/> |Called after the **BeginTrans** operation.  <br/> |
|[CommitTransComplete](begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md) <br/> |Called after the **CommitTrans** operation.  <br/> |
|[ConnectComplete](connectcomplete-and-disconnect-events-ado.md) <br/> |Called after a connection starts.  <br/> |
|[Disconnect](connectcomplete-and-disconnect-events-ado.md) <br/> |Called after a connection ends.  <br/> |
|[EndOfRecordset](endofrecordset-event-ado.md) <br/> |Called when there is an attempt to move to a row past the end of the **Recordset**.  <br/> |
|[ExecuteComplete](executecomplete-event-ado.md) <br/> |Called after a command has finished executing.  <br/> |
|[FetchComplete](fetchcomplete-event-ado.md) <br/> |Called after all the records in a lengthy asynchronous operation have been retrieved into the **Recordset**.  <br/> |
|[FetchProgress](fetchprogress-event-ado.md) <br/> |Called periodically during a lengthy asynchronous operation to report how many rows have currently been retrieved into the **Recordset**.  <br/> |
|[FieldChangeComplete](willchangefield-and-fieldchangecomplete-events-ado.md) <br/> |Called after the value of one or more **Field** objects has changed.  <br/> |
|[InfoMessage](infomessage-event-ado.md) <br/> |Called whenever a warning occurs during a **ConnectionEvent** operation.  <br/> |
|[MoveComplete](willmove-and-movecomplete-events-ado.md) <br/> |Called after the current position in the **Recordset** changes.  <br/> |
|[RecordChangeComplete](willchangerecord-and-recordchangecomplete-events-ado.md) <br/> |Called after one or more records change.  <br/> |
|[RecordsetChangeComplete](willchangerecordset-and-recordsetchangecomplete-events-ado.md) <br/> |Called after the **Recordset** has changed.  <br/> |
|[RollbackTransComplete](begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md) <br/> |Called after the **RollbackTrans** operation.  <br/> |
|[WillChangeField](willchangefield-and-fieldchangecomplete-events-ado.md) <br/> |Called before a pending operation changes the value of one or more **Field** objects in the **Recordset**.  <br/> |
|[WillChangeRecord](willchangerecord-and-recordchangecomplete-events-ado.md) <br/> |Called before one or more records (rows) in the **Recordset** change.  <br/> |
|[WillChangeRecordset](willchangerecordset-and-recordsetchangecomplete-events-ado.md) <br/> |Called before a pending operation changes the **Recordset**.  <br/> |
|[WillConnect](willconnect-event-ado.md) <br/> |Called before a connection starts.  <br/> |
|[WillExecute](willexecute-event-ado.md) <br/> |Called just before a pending command executes on this connection and affords the user an opportunity to examine and modify the pending execution parameters.  <br/> |
|[WillMove](willmove-and-movecomplete-events-ado.md) <br/> |The **WillMove** event is called  *before*  a pending operation changes the current position in the **Recordset**.  <br/> |
   

