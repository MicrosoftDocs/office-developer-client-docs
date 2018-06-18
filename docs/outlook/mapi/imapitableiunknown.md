---
title: "IMAPITable  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable
api_type:
- COM
ms.assetid: f25be2b1-0f94-4a0c-b29d-d2201dc70ab7
description: "Last modified: March 09, 2015"
---

# IMAPITable : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides a read-only view of a table. **IMAPITable** is used by clients and service providers to manipulate the way a table appears. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Table objects  <br/> |
|Implemented by:  <br/> |Service providers and MAPI  <br/> |
|Called by:  <br/> |Client applications, service providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPITable  <br/> |
|Pointer type:  <br/> |LPMAPITABLE  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetLastError](imapitable-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure containing information about the previous error on the table.  <br/> |
|[Advise](imapitable-advise.md) <br/> |Registers to receive notification of specified events affecting the table.  <br/> |
|[Unadvise](imapitable-unadvise.md) <br/> |Cancels the sending of notifications previously set up with a call to the **IMAPITable::Advise** method.  <br/> |
|[GetStatus](imapitable-getstatus.md) <br/> |Returns the table's status and type.  <br/> |
|[SetColumns](imapitable-setcolumns.md) <br/> |Defines the particular properties and order of properties to appear as columns in the table.  <br/> |
|[QueryColumns](imapitable-querycolumns.md) <br/> |Returns a list of columns for the table.  <br/> |
|[GetRowCount](imapitable-getrowcount.md) <br/> |Returns the total number of rows in the table.  <br/> |
|[SeekRow](imapitable-seekrow.md) <br/> |Moves the cursor to a specific position in the table.  <br/> |
|[SeekRowApprox](imapitable-seekrowapprox.md) <br/> |Moves the cursor to an approximate fractional position in the table.  <br/> |
|[QueryPosition](imapitable-queryposition.md) <br/> |Retrieves the current table row position of the cursor, based on a fractional value.  <br/> |
|[FindRow](imapitable-findrow.md) <br/> |Finds the next row in a table that matches specific search criteria.  <br/> |
|[Restrict](imapitable-restrict.md) <br/> |Applies a filter to a table, reducing the row set to only those rows matching the specified criteria.  <br/> |
|[CreateBookmark](imapitable-createbookmark.md) <br/> |Marks the table's current position.  <br/> |
|[FreeBookmark](imapitable-freebookmark.md) <br/> |Releases the memory associated with a bookmark.  <br/> |
|[SortTable](imapitable-sorttable.md) <br/> |Orders the rows of the table based on sort criteria.  <br/> |
|[QuerySortOrder](imapitable-querysortorder.md) <br/> |Retrieves the current sort order for a table.  <br/> |
|[QueryRows](imapitable-queryrows.md) <br/> |Returns one or more rows from a table, beginning at the current cursor position.  <br/> |
|[Abort](imapitable-abort.md) <br/> |Stops any asynchronous operations currently in progress for the table.  <br/> |
|[ExpandRow](imapitable-expandrow.md) <br/> |Expands a collapsed table category, adding the leaf rows belonging to the category to the table view.  <br/> |
|[CollapseRow](imapitable-collapserow.md) <br/> |Collapses an expanded table category, removing the leaf rows belonging to the category from the table view.  <br/> |
|[WaitForCompletion](imapitable-waitforcompletion.md) <br/> |Suspends processing until one or more asynchronous operations in progress on the table have completed.  <br/> |
|[GetCollapseState](imapitable-getcollapsestate.md) <br/> |Returns the data necessary to rebuild the current collapsed or expanded state of a categorized table.  <br/> |
|[SetCollapseState](imapitable-setcollapsestate.md) <br/> |Rebuilds the current expanded or collapsed state of a categorized table using data that was saved by a prior call to the **IMAPITable::GetCollapseState** method.  <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

