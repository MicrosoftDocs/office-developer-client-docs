---
title: "ITableDataHrDeleteRow"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ITableData.HrDeleteRow
api_type:
- COM
ms.assetid: 670c2291-d5b6-4dcf-9046-9125272dd8f8
---

# ITableData::HrDeleteRow

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Deletes a table row.
  
```cpp
HRESULT HrDeleteRow(
  LPSPropValue lpSPropValue
);
```

## Parameters

 _lpSPropValue_
  
> [in] A pointer to a property value structure that describes the index column for the row to be deleted. The **ulPropTag** member of the property value structure should contain the same property tag as the  _ulPropTagIndexColumn_ parameter from the call to the [CreateTable](createtable.md) function. 
    
## Return value

S_OK 
  
> The row was successfully deleted.
    
MAPI_E_NOT_FOUND 
  
> The property pointed to by the  _lpSPropValue_ parameter does not identify a row in the table. 
    
## Remarks

The **ITableData::HrDeleteRow** method removes the table row that contains the column that matches the property pointed to by the  _lpSPropValue_ parameter. The data for the row is deleted and the row is removed from all open views. 
  
After the row is deleted, notifications are sent to all clients or service providers that have a view of the table and that have called the table's [IMAPITable::Advise](imapitable-advise.md) method to register for notifications. 
  
Deleting a row does not reduce the column set that is available to existing views or subsequently opened views, even if the deleted row is the last row that has a value for a specific column.
  
## See also



[CreateTable](createtable.md)
  
[ITableData::HrDeleteRows](itabledata-hrdeleterows.md)
  
[ITableData::HrModifyRow](itabledata-hrmodifyrow.md)
  
[SPropValue](spropvalue.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

