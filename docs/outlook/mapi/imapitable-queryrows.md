---
title: "IMAPITableQueryRows"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.QueryRows
api_type:
- COM
ms.assetid: f26384f1-467e-4343-92b3-0425da9d2123
description: "Last modified: March 09, 2015"
---

# IMAPITable::QueryRows

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Returns one or more rows from a table, beginning at the current cursor position.
  
```
HRESULT QueryRows(
LONG lRowCount,
ULONG ulFlags,
LPSRowSet FAR * lppRows
);
```

## Parameters

 _lRowCount_
  
> [in] Maximum number of rows to be returned.
    
 _ulFlags_
  
> [in] Bitmask of flags that control how rows are returned. The following flag can be set:
    
TBL_NOADVANCE 
  
> Prevents the cursor from advancing as a result of the row retrieval. If the TBL_NOADVANCE flag is set, the cursor points to the first row returned. If the TBL_NOADVANCE flag is not set, the cursor points to the row following the last row returned.
    
 _lppRows_
  
> [out] Pointer to a pointer to an [SRowSet](srowset.md) structure holding the table rows. 
    
## Return value

S_OK 
  
> The rows were successfully returned.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the row retrieval operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
MAPI_E_INVALID_PARAMETER 
  
> The  _IRowCount_ parameter is set to zero. 
    
## Remarks

The **IMAPITable::QueryRows** method gets one or more rows of data from a table. The value of the  _IRowCount_ parameter affects the starting point for the retrieval. If  _IRowCount_ is positive, rows are read in a forward direction, starting at the current position. If  _IRowCount_ is negative, **QueryRows** resets the starting point by moving backward the indicated number of rows. After the cursor is reset, rows are read in forward order. 
  
The **cRows** member in the [SRowSet](srowset.md) structure pointed to by the  _lppRows_ parameter indicates the number of rows returned. If zero rows are returned: 
  
- The cursor was already positioned at the beginning of the table and the value of  _IRowCount_ is negative. -Or- 
    
- The cursor was already positioned at the end of the table and the value of  _IRowCount_ is positive. 
    
The number of columns and their ordering is the same for each row. If a property does not exist for a row or there is an error reading a property, the **SPropValue** structure for the property in the row contains the following values: 
  
- PT_ERROR for the property type in the **ulPropTag** member. 
    
- MAPI_E_NOT_FOUND for the **Value** member. 
    
Memory used for the [SPropValue](spropvalue.md) structures in the row set pointed to by the  _lppRows_ parameter must be separately allocated and freed for each row. Use [MAPIFreeBuffer](mapifreebuffer.md) to free the property value structures and to free the row set. When a call to **QueryRows** returns zero, however, indicating the beginning or end of the table, only the **SRowSet** structure itself needs to be freed. For more information about how to allocate and free memory in an **SRowSet** structure, see [Managing Memory for ADRLIST and SRowSet Structures](managing-memory-for-adrlist-and-srowset-structures.md).
  
The rows that are returned and the order in which they are returned depend on whether or not successful calls have been made to [IMAPITable::Restrict](imapitable-restrict.md) and [IMAPITable::SortTable](imapitable-sorttable.md). **Restrict** filters rows from the view, causing **QueryRows** to return only the rows that match the criteria specified in the restriction. **SortTable** establishes a standard or categorized sort order, affecting the sequence of rows returned by **QueryRows**. The returned rows are in the order specified in the [SSortOrderSet](ssortorderset.md) structure passed to **SortTable**.
  
The columns returned for each row and the order in which they are returned depend on whether or not a successful call has been made to [IMAPITable::SetColumns](imapitable-setcolumns.md). **SetColumns** establishes a column set, specifying the properties to be included in columns in the table and the order in which they should be included. If a **SetColumns** call has been made, the particular columns in each row and the order of those columns match the column set specified in the call. If no **SetColumns** call has been made, the table returns its default column set. 
  
If none of these calls has been made, **QueryRows** returns all of the rows in the table. Each row contains the default column set in default order. 
  
When the column set established in a call to [IMAPITable::SetColumns](imapitable-setcolumns.md) includes columns set to PR_NULL, the [SPropValue](spropvalue.md) array within the row set returned in  _lppRows_ will contain empty slots. 
  
## Notes to Implementers

You can allow a caller to request an unsupported column to be included in the column set. When this occurs, place PT_ERROR in the property type portion of the property tag and MAPI_E_NOT_FOUND in the property value for the unsupported column. 
  
Treat the row count as a request rather than a requirement. You can return anywhere from zero rows, if there are no rows in the direction of the query, to the number requested. 
  
Return only the rows that the user will see when rows are requested from a categorized table view, allowing the caller to make valid assumptions about the scope of the data and avoid extra work. 
  
## Notes to Callers

Usually you will end up with as many rows as you have specified in the  _lRowCount_ parameter. However, when memory or implementation limits are an issue or when the operation reaches the beginning or end of the table prematurely, **QueryRows** will return less rows than requested. 
  
If **QueryRows** returns MAPI_E_BUSY, call the [IMAPITable::WaitForCompletion](imapitable-waitforcompletion.md) method and retry the call to **QueryRows** when the asynchronous operation is complete. 
  
When calling **QueryRows**, be aware that the timing of asynchronous notifications can potentially cause the row set that you get back from **QueryRows** not to accurately represent the underlying data. For example, a call to **QueryRows** to a folder's contents table following the deletion of a message but prior to the receipt of the corresponding notification will cause the deleted row to be returned in the row set. Always wait for a notification to arrive before updating the user's view of the data. 
  
For more information about retrieving rows from tables, see [Retrieving Data from Table Rows](retrieving-data-from-table-rows.md).
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |DwThreadFuncLoadTable  <br/> |MFCMAPI uses the **IMAPITable::QueryRows** method to retrieve rows in the table to load into the view.  <br/> |
   
## See also

#### Reference

[ADRENTRY](adrentry.md)
  
[FreeProws](freeprows.md)
  
[HrQueryAllRows](hrqueryallrows.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[IMAPITable::WaitForCompletion](imapitable-waitforcompletion.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SRow](srow.md)
  
[SRowSet](srowset.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

