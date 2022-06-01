---
title: "IMAPITableGetRowCount"
description: "Describes the syntax, parameters, and return value of IMAPITableGetRowCount, which returns the total number of rows in the table."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.GetRowCount
api_type:
- COM
ms.assetid: 44a12c92-7462-4acf-9520-5d4c2d7f1d47
---

# IMAPITable::GetRowCount

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the total number of rows in the table. 
  
```cpp
HRESULT GetRowCount(
ULONG ulFlags,
ULONG FAR * lpulCount
);
```

## Parameters

 _ulFlags_
  
> Reserved; must be zero.
    
 _lpulCount_
  
> [out] Pointer to the number of rows in the table.
    
## Return value

S_OK 
  
> The row count was successfully returned.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the row count retrieval operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
MAPI_E_NO_SUPPORT 
  
> The table cannot calculate the number of rows.
    
MAPI_W_APPROX_COUNT 
  
> The call succeeded, but an approximate row count was returned because the exact row count could not be determined possibly due to memory constraints. To test for this warning, use the **HR_FAILED** macro. See [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPITable::GetRowCount** method retrieves the total number of rows in a table. 
  
## Notes to implementers

If you cannot determine the table's exact row count, return MAPI_W_APPROX_COUNT and an approximate row count in the contents of the  _lpulCount_ parameter. 
  
## Notes to callers

Use **GetRowCount** to find out how many rows a table holds before making a call to the [IMAPITable::QueryRows](imapitable-queryrows.md) method to retrieve the data. If there are less than twenty rows in the table, it is safe to call **QueryPosition** to retrieve the whole table. If there are more than twenty rows in the table, consider making multiple calls to **QueryPosition** and limit the number of rows retrieved in each call. 
  
Some tables do not support **GetRowCount** and return MAPI_E_NO_SUPPORT. If **GetRowCount** is not supported, an alternative might be to call [IMAPITable::QueryPosition](imapitable-queryposition.md). With the results from **QueryPosition**, you can determine the relationship between the current row and last row. 
  
When **GetRowCount** returns MAPI_E_BUSY because it is temporarily unable to retrieve a row count, call the [IMAPITable::WaitForCompletion](imapitable-waitforcompletion.md) method. When **WaitForCompletion** returns, retry the call to **GetRowCount**. Another way to detect whether an asynchronous operation is in progress is to call the [IMAPITable::GetStatus](imapitable-getstatus.md) method and check the contents of the  _lpulTableState_ parameter. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |CopyFolderContents  <br/> |MFCMAPI uses the **IMAPITable::GetRowCount** method to determine how many rows are in the source table so memory can be allocated to perform the copy. |
   
## See also



[IMAPITable::GetStatus](imapitable-getstatus.md)
  
[IMAPITable::QueryPosition](imapitable-queryposition.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::WaitForCompletion](imapitable-waitforcompletion.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

