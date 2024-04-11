---
title: "IMAPITableQueryColumns"
description: "Describes the syntax, parameters, and return value of IMAPITable QueryColumns, which returns a list of columns for the table."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.QueryColumns
api_type:
- COM
ms.assetid: d6341acc-c6ca-4605-93af-77230040339d
---

# IMAPITable::QueryColumns

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a list of columns for the table.
  
```cpp
HRESULT QueryColumns(
ULONG ulFlags,
LPSPropTagArray FAR * lpPropTagArray
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags that indicates which column set should be returned. The following flag can be set:
    
TBL_ALL_COLUMNS 
  
> The table should return all available columns.
    
 _lpPropTagArray_
  
> [out] Pointer to an [SPropTagArray](sproptagarray.md) structure containing the property tags for the column set. 
    
## Return value

S_OK 
  
> The column set was successfully returned.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the column set retrieval operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
## Remarks

The **IMAPITable::QueryColumns** method can be called to retrieve: 
  
- The default column set for a table.
    
- The current column set for a table, as established by a call to the [IMAPITable::SetColumns](imapitable-setcolumns.md) method. 
    
- The complete column set for a table, the columns that are available, but not necessarily part of the current set.
    
## Notes to callers

If you do not set the TBL_ALL_COLUMNS flag, **IMAPITable::QueryColumns** returns either a table's default or current column set, depending on whether the table has been affected by a call to **IMAPITable::SetColumns**. **SetColumns** changes the order and selection of columns in a table's column set. 
  
If you set the TBL_ALL_COLUMNS flag, **QueryColumns** returns all of the columns that are capable of being in the table's column set. 
  
Free the memory for the property tag array pointed to by the  _lpPropTagArray_ parameter by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::DoSetColumns  <br/> |MFCMAPI uses the **IMAPITable::QueryColumns** method to retrieve the current column set for a table so the user can edit it. |
   
## See also



[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropTagArray](sproptagarray.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

