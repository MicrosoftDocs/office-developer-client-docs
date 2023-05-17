---
title: "ITableDataHrQueryRow"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ITableData.HrQueryRow
api_type:
- COM
ms.assetid: 66ce8f36-2b2b-4a8e-b9b2-43782d8357a1
---

# ITableData::HrQueryRow

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves a table row.
  
```cpp
HRESULT HrQueryRow(
  LPSPropValue lpSPropValue,
  LPSRow FAR * lppSRow,
  ULONG FAR * lpuliRow
);
```

## Parameters

 _lpSPropValue_
  
> [in] A pointer to a property value structure that describes the index column for the row to be retrieved. The **ulPropTag** member of the property value structure should contain the same property tag as the  _ulPropTagIndexColumn_ parameter from the call to the [CreateTable](createtable.md) function, which accesses the [ITableData](itabledataiunknown.md) implementation. 
    
 _lppSRow_
  
> [out] A pointer to a pointer to the retrieved row. 
    
 _lpuliRow_
  
> [in, out] On input, a valid pointer or NULL, which indicates that no information needs to be returned. On output, a valid pointer that points to the row's row number, a sequential number that identifies the row's position in the table.
    
## Return value

S_OK 
  
> The row was successfully retrieved.
    
MAPI_E_INVALID_PARAMETER 
  
> The [SPropValue](spropvalue.md) structure that  _lpSPropValue_ points to does not contain the index column property. 
    
## Remarks

The **ITableData::HrQueryRow** method retrieves all of the properties for the row that has an index column that matches the value of the index column included in the property structure pointed to by  _lpSPropValue_. **HrQueryRow** also returns the row number, if the caller requests it, that identifies the row's position in the table. 
  
Because **HrQueryRow** does not modify the **SPropValue** structure pointed to by  _lpSPropValue_, callers must free the structure when **HrQueryRow** returns. Callers must also free the **SRow** structure that contains the retrieved row. 
  
## See also



[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropValue](spropvalue.md)
  
[SRow](srow.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

