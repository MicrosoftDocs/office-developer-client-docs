---
title: "IMAPITableSortTable"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.SortTable
api_type:
- COM
ms.assetid: ff5f78ac-06cf-46fb-93da-5f4a3a5d1b22
description: "Last modified: July 23, 2011"
---

# IMAPITable::SortTable

**Applies to**: Outlook 
  
The **IMAPITable::SortTable** method orders the rows of the table, depending on sort criteria. 
  
```
HRESULT SortTable(
LPSSortOrderSet lpSortCriteria,
ULONG ulFlags
);
```

## Parameters

_lpSortCriteria_
  
> [in] Pointer to an [SSortOrderSet](ssortorderset.md) structure that contains the sort criteria to apply. Passing an **SSortOrderSet** structure that contains zero columns indicates that the table does not have to be sorted in any particular order. 
    
_ulFlags_
  
> [in] Bitmask of flags that controls the timing of the **IMAPITable::SortTable** operation. The following flags can be set: 
    
TBL_ASYNC 
  
> Starts the operation asynchronously and returns before the operation is complete.
    
TBL_BATCH 
  
> Defers the completion of the sort until the data in the table is required.
    
## Return value

S_OK 
  
> The sort operation was successful.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the sort operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
MAPI_E_NO_SUPPORT 
  
> The table does not support the type of sorting requested.
    
MAPI_E_TOO_COMPLEX 
  
> The table cannot perform the operation because the particular sort criteria pointed to by the  _lpSortCriteria_ parameter is too complex. **SortTable** can return MAPI_E_TOO_COMPLEX under the following conditions. 
    
   - A sort operation is requested for a property column that the implementation cannot sort.
    
   - The implementation does not support the sort order requested in the **ulOrder** member of the **SSortOrderSet** structure. 
    
   - The number of columns to be sorted, as specified in the **cSorts** member in **SSortOrderSet**, is larger than the implementation can handle.
    
   - A sort operation is requested, as indicated by a property tag in **SSortOrderSet**, based on a property that is not in the available or active set and the implementation does not support sorting on properties not in the available set.
    
   - One property is specified multiple times in a sort order set, as indicated by multiple instances of the same property tag, and the implementation cannot perform such a sort operation.
    
   - A sort operation based on multivalued property columns is requested using MVI_FLAG and the implementation does not support sorting on multivalued properties. 
    
   - A property tag for a property in **SSortOrderSet** specifies a property or type that the implementation does not support. 
    
   - A sort operation other than one that proceeds through the table from the **PR_RENDERING_POSITION** ([PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md)) property forward is specified only for an attachment table that supports this type of sorting.
    
## Remarks

The **IMAPITable::SortTable** method orders the rows in a table view. Whereas some tables support both standard and categorized sorting on various sort key columns, other tables are more limited in their support. Address book providers ordinarily do not support table sorting. Message store providers usually support sorting to the extent that they keep the sort order of folders that results when a full table (a table without restrictions) is sorted. 
  
Some tables allow sorting to be done on any table column. Other tables do not; columns not included in the table view are unaffected by a **SortTable** call. Some tables require that sort keys be built only with columns in the table's current column set. 
  
A table can return either MAPI_E_NO_SUPPORT or MAPI_E_TOO_COMPLEX from **SortTable** when it cannot complete a sort operation. Moreover, store providers are not guaranteed to honor the sort order set specified for hierarchy tables. 
  
When there are zero columns in the [SSortOrderSet](ssortorderset.md) structure pointed to by the  _lpSortCriteria_ parameter, the table returns the current column set. The current sort order can be retrieved by calling the table's [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) method. 
  
All bookmarks for a table are invalidated and should be deleted when a call to **SortTable** is made, and the BOOKMARK_CURRENT bookmark that indicates the current cursor position, should be set to the beginning of the table. 
  
If you are sorting on a column that contains a multivalued property without the MVI_FLAG flag set, the column's values are treated as a completely ordered tuple. A comparison of two multivalued columns compares the column elements in order, reporting the relation of the columns at the first inequality, and returns equality only if the columns being compared contain the same values in the same order. If one column has fewer values than the other, the reported relation is that of a null value to the other value.
  
## Notes to callers

**SortTable** operates synchronously unless you set one of the flags. If you set the TBL_BATCH flag, **SortTable** postpones the sort operation unless you request the data. If the TBL_ASYNC flag is set, **SortTable** operates asynchronously, potentially returning before the completion of the operation. 
  
Call the [IMAPITable::Abort](imapitable-abort.md) method to stop an asynchronous operation in progress if your sort must be done immediately. If **SortTable** cannot continue because one or more asynchronous operations on the table are in progress, it returns MAPI_E_BUSY. 
  
For best performance, call **SetColumns** to customize the table's column set and **Restrict** to limit the number of rows in the table before you call **SortTable** to perform the sort. 
  
Whenever **SortTable** fails, the sort order that was in effect before the failure is still in effect. 
  
## See also

- [IMAPITable::Abort](imapitable-abort.md)
- [IMAPITable::GetRowCount](imapitable-getrowcount.md)
- [IMAPITable::QueryColumns](imapitable-querycolumns.md)
- [IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
- [IMAPITable::SetColumns](imapitable-setcolumns.md)
- [SSortOrderSet](ssortorderset.md)
- [IMAPITable : IUnknown](imapitableiunknown.md)

