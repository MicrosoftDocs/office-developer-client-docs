---
title: "ITableDataHrModifyRows"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ITableData.HrModifyRows
api_type:
- COM
ms.assetid: d295c896-9882-4d6f-9689-5cf40db208c0
---

# ITableData::HrModifyRows

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Inserts multiple table rows, possibly replacing existing rows.
  
```cpp
HRESULT HrModifyRows(
  ULONG ulFlags,
  LPSRowSet lpSRowSet
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpSRowSet_
  
> [in] A pointer to an [SRowSet](srowset.md) structure that contains the set of rows to be added, replacing existing rows if necessary. One of the property value structures pointed to by the **lpProps** member of each [SRow](srow.md) structure in the row set should contain the index column, the same value that was specified in the _ulPropTagIndexColumn_ parameter in the call to the [CreateTable](createtable.md) function. 
    
## Return value

S_OK 
  
> The rows were successfully inserted or modified.
    
MAPI_E_INVALID_PARAMETER 
  
> One or more of the passed-in rows does not have an index column. If this error is returned, no rows are changed.
    
## Remarks

The **ITableData::HrModifyRows** method inserts the rows described by the [SRowSet](srowset.md) structure pointed to by the  _lpSRowSet_ parameter. If the index column value of a row in the row set matches the value for an existing row in the table, the existing row is replaced. If no row exists that matches the one included in the **SRowSet** structure, **HrModifyRows** adds the row to the end of the table. 
  
All views of the table are modified to include the rows pointed to by  _lpSRowSet_. However, if a view has a restriction in place that excludes a row, it may not be visible to the user. 
  
The columns in the rows pointed to by  _lpSRowSet_ do not have to be in the same order as the columns in the table. The caller can also include as columns properties that are not currently in the table. For existing views, **HrModifyRows** makes these new columns available but does not include them in the current column set. For future views, **HrModifyRows** includes the new columns in the column set. 
  
After **HrModifyRows** has added the rows, notifications are sent to all clients or service providers that have a view of the table and that have called the table's [IMAPITable::Advise](imapitable-advise.md) method to register for notifications. MAPI sends TABLE_ROW_ADDED or TABLE_ROW_MODIFIED notifications for each row, up to eight rows. If more than eight rows are affected by the **HrModifyRows** call, MAPI sends a single TABLE_CHANGED notification instead. 
  
## See also



[SRowSet](srowset.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

