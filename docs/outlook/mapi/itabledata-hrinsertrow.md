---
title: "ITableDataHrInsertRow"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITableData.HrInsertRow
api_type:
- COM
ms.assetid: e5ae37ea-81a5-49c7-9ad0-0bfac518426c
description: "Last modified: July 23, 2011"
---

# ITableData::HrInsertRow

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Inserts a table row. 
  
```cpp
HRESULT HrInsertRow(
  ULONG uliRow,
  LPSRow lpSRow
);
```

## Parameters

 _uliRow_
  
> [in] A sequential row number that represents a specific row. The new row will be placed after the row that the number indicates. The  _uliRow_ parameter can contains row numbers from 0 through n, where n is the total number of rows in the table. Passing n in  _uliRow_ appends the row to the end of the table. 
    
 _lpSRow_
  
> [in] A pointer to an [SRow](srow.md) structure that describes the row to be inserted. 
    
## Return value

S_OK 
  
> The row was successfully inserted.
    
MAPI_E_INVALID_PARAMETER 
  
> A row that has the same value for its index column as the row to be inserted already exists in the table.
    
## Remarks

The **ITableData::HrInsertRow** method inserts a row into a table at a particular position. The new row is inserted after the row that is in the position specified by the  _uliRow_ parameter. 
  
If  _uliRow_ is set to the number of rows in the table, the new row is appended to the end of the table. 
  
The property that acts as the index column for the table must be included in the **lpProps** member of the [SRow](srow.md) structure pointed to by the  _lpSRow_ parameter. This index property, typically **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)), is used to uniquely identify the row for future maintenance tasks.
  
The property columns in the **SRow** structure do not have to be in the same order as the property columns in the table. 
  
After the row is inserted, notifications are sent to all clients or service providers that have a view of the table and that have called the table's [IMAPITable::Advise](imapitable-advise.md) method to register for notifications. No notification is sent if the inserted row is not included in the view due to a restriction. 
  
## See also



[SRow](srow.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

