---
title: "ITableData  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITableData
api_type:
- COM
ms.assetid: ac7ae09f-ce19-45cf-8963-fad5bba75452
description: "Last modified: March 09, 2015"
---

# ITableData : IUnknown

  
  
**Applies to**: Outlook 
  
Provides utility methods for working with tables. MAPI provides table data objects or objects that implement **ITableData** to help service providers perform table maintenance. To obtain a table data object, service providers call the [CreateTable](createtable.md) function. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Exposed by:  <br/> |Table data objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPITableData  <br/> |
|Pointer type:  <br/> |LPTABLEDATA  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[HrGetView](itabledata-hrgetview.md) <br/> |Creates a table view, returning a pointer to an [IMAPITable](imapitableiunknown.md) implementation.  <br/> |
|[HrModifyRow](itabledata-hrmodifyrow.md) <br/> |Inserts a new table row, possibly replacing an existing row.  <br/> |
|[HrDeleteRow](itabledata-hrdeleterow.md) <br/> |Deletes a table row.  <br/> |
|[HrQueryRow](itabledata-hrqueryrow.md) <br/> |Retrieves a table row.  <br/> |
|[HrEnumRow](itabledata-hrenumrow.md) <br/> |Retrieves a row based on its position in the table.  <br/> |
|[HrNotify](itabledata-hrnotify.md) <br/> |Sends a notification for a table row.  <br/> |
|[HrInsertRow](itabledata-hrinsertrow.md) <br/> |Inserts a table row.  <br/> |
|[HrModifyRows](itabledata-hrmodifyrows.md) <br/> |Inserts multiple table rows, possibly replacing existing rows.  <br/> |
|[HrDeleteRows](itabledata-hrdeleterows.md) <br/> |Deletes multiple table rows.  <br/> |
   
## Remarks

The MAPI implementation of **ITableData** works with tables by holding all of the data and any associated restrictions in memory, making it unsuitable for use with very large tables. Large restrictions and complex operations such as categorization are not supported. 
  
Table data objects identify rows by using an index column, a property that is guaranteed to have a unique value for each row. Most service providers use the **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) property as the index column. Properties that have multiple values cannot be used as an index column.
  
Table data objects generate a single notification regardless of the number of rows affected by a change or deletion. If a target row in an operation does not exist, a row is added.
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

