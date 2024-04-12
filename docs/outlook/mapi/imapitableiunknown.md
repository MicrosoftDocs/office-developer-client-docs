---
title: "IMAPITable  IUnknown"
description: "IMAPITable IUnknown provides a read-only view of a table. IMAPITable is used by clients and service providers to manipulate the way a table appears."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable
api_type:
- COM
ms.assetid: f25be2b1-0f94-4a0c-b29d-d2201dc70ab7
---

# IMAPITable : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides a read-only view of a table. **IMAPITable** is used by clients and service providers to manipulate the way a table appears. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Table objects  <br/> |
|Implemented by:  <br/> |Service providers and MAPI  <br/> |
|Called by:  <br/> |Client applications, service providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPITable  <br/> |
|Pointer type:  <br/> |LPMAPITABLE  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[GetLastError](imapitable-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure containing information about the previous error on the table. |
|[Advise](imapitable-advise.md) <br/> |Registers to receive notification of specified events affecting the table. |
|[Unadvise](imapitable-unadvise.md) <br/> |Cancels the sending of notifications previously set up with a call to the **IMAPITable::Advise** method. |
|[GetStatus](imapitable-getstatus.md) <br/> |Returns the table's status and type. |
|[SetColumns](imapitable-setcolumns.md) <br/> |Defines the particular properties and order of properties to appear as columns in the table. |
|[QueryColumns](imapitable-querycolumns.md) <br/> |Returns a list of columns for the table. |
|[GetRowCount](imapitable-getrowcount.md) <br/> |Returns the total number of rows in the table. |
|[SeekRow](imapitable-seekrow.md) <br/> |Moves the cursor to a specific position in the table. |
|[SeekRowApprox](imapitable-seekrowapprox.md) <br/> |Moves the cursor to an approximate fractional position in the table. |
|[QueryPosition](imapitable-queryposition.md) <br/> |Retrieves the current table row position of the cursor, based on a fractional value. |
|[FindRow](imapitable-findrow.md) <br/> |Finds the next row in a table that matches specific search criteria. |
|[Restrict](imapitable-restrict.md) <br/> |Applies a filter to a table, reducing the row set to only those rows matching the specified criteria. |
|[CreateBookmark](imapitable-createbookmark.md) <br/> |Marks the table's current position. |
|[FreeBookmark](imapitable-freebookmark.md) <br/> |Releases the memory associated with a bookmark. |
|[SortTable](imapitable-sorttable.md) <br/> |Orders the rows of the table based on sort criteria. |
|[QuerySortOrder](imapitable-querysortorder.md) <br/> |Retrieves the current sort order for a table. |
|[QueryRows](imapitable-queryrows.md) <br/> |Returns one or more rows from a table, beginning at the current cursor position. |
|[Abort](imapitable-abort.md) <br/> |Stops any asynchronous operations currently in progress for the table. |
|[ExpandRow](imapitable-expandrow.md) <br/> |Expands a collapsed table category, adding the leaf rows belonging to the category to the table view. |
|[CollapseRow](imapitable-collapserow.md) <br/> |Collapses an expanded table category, removing the leaf rows belonging to the category from the table view. |
|[WaitForCompletion](imapitable-waitforcompletion.md) <br/> |Suspends processing until one or more asynchronous operations in progress on the table have completed. |
|[GetCollapseState](imapitable-getcollapsestate.md) <br/> |Returns the data necessary to rebuild the current collapsed or expanded state of a categorized table. |
|[SetCollapseState](imapitable-setcollapsestate.md) <br/> |Rebuilds the current expanded or collapsed state of a categorized table using data that was saved by a prior call to the **IMAPITable::GetCollapseState** method. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

