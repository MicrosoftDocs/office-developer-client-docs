---
title: "ITableDataHrEnumRow"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITableData.HrEnumRow
api_type:
- COM
ms.assetid: b25d9f2b-9454-4983-98f7-6a051a3b8a04
description: "Last modified: July 23, 2011"
---

# ITableData::HrEnumRow

  
  
**Applies to**: Outlook 
  
Retrieves a row based on its position in the table. 
  
```cpp
HRESULT HrEnumRow(
  ULONG ulRowNumber,
  LPSRow FAR * lppSRow
);
```

## Parameters

 _ulRowNumber_
  
> [in] The number of the row for which to return properties. The value in the  _ulRowNumber_ parameter can be any value from 0, which indicates the first row in the table, through n - 1, which indicates the last row in the table. 
    
 _lppSRow_
  
> [out] A pointer to a pointer to an [SRow](srow.md) structure that describes the target row. 
    
## Return value

S_OK 
  
> The row was retrieved successfully, or a row for the row number specified by the  _ulRowNumber_ parameter does not exist. 
    
## Remarks

The **ITableData::HrEnumRow** method retrieves a row based on a sequential number. This number represents the order of insertion (0 indicates the first row, and the number of rows minus 1 indicates the last row). MAPI maintains this chronological order of row insertion for the lifetime of the table data object. 
  
If the number specified in  _ulRowNumber_ does not correspond to a row in the table, **HrEnumRow** returns S_OK and sets the  _lppSRow_ parameter to NULL. 
  
MAPI allocates memory for the returned **SRow** structure by using the [MAPIAllocateBuffer](mapiallocatebuffer.md) function when the table data object is created. The caller must release this memory by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
To retrieve rows from a table in the order that they were inserted, table data object users call the **HrEnumRow** method. 
  
## See also



[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SRow](srow.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

