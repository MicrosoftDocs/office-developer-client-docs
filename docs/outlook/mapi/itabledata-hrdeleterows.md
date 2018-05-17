---
title: "ITableDataHrDeleteRows"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITableData.HrDeleteRows
api_type:
- COM
ms.assetid: 7b351eec-9624-4b38-9978-5d0b67b64687
description: "Last modified: July 23, 2011"
---

# ITableData::HrDeleteRows

  
  
**Applies to**: Outlook 
  
Deletes multiple table rows.
  
```
HRESULT HrDeleteRows(
  ULONG ulFlags,
  LPSRowSet lprowsetToDelete,
  ULONG FAR * cRowsDeleted
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the deletion. The following flag can be set:
    
TAD_ALL_ROWS 
  
> Deletes all rows from the table and all corresponding views, sending a single TABLE_RELOAD notification.
    
 _lprowsetToDelete_
  
> [in] A pointer to a row set that describes the rows to be deleted. The  _lprowsetToDelete_ parameter can be NULL if the TAD_ALL_ROWS flag is set in the  _ulFlags_ parameter. 
    
 _cRowsDeleted_
  
> [out] The count of the deleted rows.
    
## Return value

S_OK 
  
> The table rows were successfully deleted.
    
## Remarks

The **ITableData::HrDeleteRows** method locates and removes the table rows that contain the columns that match the property pointed to by the **lpProps** member of each **aRow** entry in the row set. An index column is used to identify each row; this column must have the same property tag as the property tag passed in the  _ulPropTagIndexColumn_ parameter in the call to the [CreateTable](createtable.md) function. 
  
The number of rows that were actually deleted is returned in  _cRowsDeleted_. No error is returned if one or more rows could not be found. 
  
After the rows are deleted, notifications are sent to all clients or service providers that have a view of the table and that have called the table's [IMAPITable::Advise](imapitable-advise.md) method to register for notifications. 
  
Deleting rows does not reduce the columns available to existing table views or subsequently opened table views, even if the deleted rows are the last that have values for a specific column.
  
## See also

#### Reference

[CreateTable](createtable.md)
  
[ITableData::HrDeleteRow](itabledata-hrdeleterow.md)
  
[ITableData::HrModifyRows](itabledata-hrmodifyrows.md)
  
[SRowSet](srowset.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

