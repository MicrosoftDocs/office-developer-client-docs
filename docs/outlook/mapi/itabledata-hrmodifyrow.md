---
title: "ITableDataHrModifyRow"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ITableData.HrModifyRow
api_type:
- COM
ms.assetid: 9e255b3e-dd17-4528-ba4e-c3a1aef32b04
---

# ITableData::HrModifyRow

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Inserts a new table row, possibly replacing an existing row.
  
```cpp
HRESULT HrModifyRow(
  LPSRow lpSRow
);
```

## Parameters

 _lpSRow_
  
> [in] A pointer to an [SRow](srow.md) structure that describes the row to be added or to replace an existing row. One of the property value structures pointed to by the **lpProps** member of the **SRow** structure should contain the index column, the same value that was specified in the _ulPropTagIndexColumn_ parameter in the call to the [CreateTable](createtable.md) function. 
    
## Return value

S_OK 
  
> The row was successfully inserted or modified.
    
MAPI_E_INVALID_PARAMETER 
  
> The passed-in row does not have an index column.
    
## Remarks

The **ITableData::HrModifyRow** method inserts the row described by the **SRow** structure pointed to by the  _lpSRow_ parameter. If a row that has the same value for its index column as the row that  _lpSRow_ points to already exists in the table, the existing row is replaced. If no row exists that matches the one included in the **SRow** structure, **HrModifyRow** adds the row to the end of the table. 
  
All views of the table are modified to include the row pointed to by  _lpSRow_. However, if a view has a restriction in place that excludes the row, it may not be visible to the user. 
  
The columns in the row pointed to by  _lpSRow_ do not have to be in the same order as the columns in the table. The caller can also include as columns properties that are not currently in the table. For existing views, **HrModifyRow** makes these new columns available but does not include them in the current column set. For future views, **HrModifyRow** includes the new columns in the column set. 
  
After **HrModifyRow** adds the row, notifications are sent to all clients or service providers that have a view of the table and that have called the table's [IMAPITable::Advise](imapitable-advise.md) method to register for notifications. 
  
## See also



[SRow](srow.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

