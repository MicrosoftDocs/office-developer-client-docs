---
title: "ADO Event Handler Summary"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: f50b9eb4-df6e-7b9d-0b3d-dca8945167a2
description: "Two ADO objects can raise events: the Connection object and the Recordset object. The ConnectionEvent family pertains to operations on the Connection object, and the RecordsetEvent family pertains to operations on the Recordset object."
---

# ADO Event Handler Summary

Two ADO objects can raise events: the [Connection](connection-object-ado.md) object and the [Recordset](recordset-object-ado.md) object. The **ConnectionEvent** family pertains to operations on the **Connection** object, and the **RecordsetEvent** family pertains to operations on the **Recordset** object. 
  
- **Connection Events**: Events are issued when a transaction on a connection begins, is committed, or is rolled back; when a [Command](command-object-ado.md) executes; when a warning occurs during a **Connection Event** operation; or when a **Connection** starts or ends. 
    
- **Recordset Events**: Events are issued around asynchronous fetch operations as well as when you navigate through the rows of a **Recordset** object, change a field in a row of a **Recordset**, change a row in a **Recordset**, open a **Recordset** with a server-side cursor, close a **Recordset**, or make any change whatsoever in the **Recordset**. 
    
The following tables summarize the events and their descriptions.
  
|**ConnectionEvent**|**Description**|
|:-----|:-----|
|[BeginTransComplete](begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md), CommitTransComplete, RollbackTransComplete  <br/> |**Transaction Management** — Notification that the current transaction on the connection has started, committed, or rolled back.  <br/> |
|[WillConnect](willconnect-event-ado.md), [ConnectComplete, Disconnect](connectcomplete-and-disconnect-events-ado.md) <br/> |**Connection Management** — Notification that the current connection will start, has started, or has ended.  <br/> |
|[WillExecute](willexecute-event-ado.md), [ExecuteComplete](executecomplete-event-ado.md) <br/> |**Command Execution Management** — Notification that the execution of the current command on the connection will start or has ended.  <br/> |
|[InfoMessage](infomessage-event-ado.md) <br/> |**Informational** — Notification that there is additional information about the current operation.  <br/> |
   
|**RecordsetEvent**|**Description**|
|:-----|:-----|
|[FetchProgress](fetchprogress-event-ado.md), [FetchComplete](fetchcomplete-event-ado.md) <br/> |**Retrieval Status** — Notification of the progress of a data retrieval operation, or that the retrieval operation has completed. These events are only available if the **Recordset** was opened using a client-side cursor.  <br/> |
|[WillChangeField, FieldChangeComplete](willchangefield-and-fieldchangecomplete-events-ado.md) <br/> |**Field Change Management** — Notification that the value of the current field will change, or has changed.  <br/> |
|[WillMove, MoveComplete](willmove-and-movecomplete-events-ado.md), [EndOfRecordset](endofrecordset-event-ado.md) <br/> |**Navigation Management** — Notification that the current row position in a **Recordset** will change, has changed, or has reached the end of the **Recordset**.  <br/> |
|[WillChangeRecord, RecordChangeComplete](willchangerecord-and-recordchangecomplete-events-ado.md) <br/> |**Row Change Management** — Notification that something in the current row of the **Recordset** will change, or has changed.  <br/> |
|[WillChangeRecordset, RecordsetChangeComplete](willchangerecordset-and-recordsetchangecomplete-events-ado.md) <br/> |**Recordset Change Management** — Notification that something in the current **Recordset** will change, or has changed.  <br/> |
   

