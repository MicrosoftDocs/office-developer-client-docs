---
title: "IMAPITableGetStatus"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.GetStatus
api_type:
- COM
ms.assetid: f114f1fa-bc05-4587-875b-71548c5912ea
description: "Last modified: March 09, 2015"
---

# IMAPITable::GetStatus

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the table's status and type.
  
```cpp
HRESULT GetStatus(
ULONG FAR * lpulTableStatus,
ULONG FAR * lpulTableType
);
```

## Parameters

 _lpulTableStatus_
  
> [out] Pointer to a value indicating the status of the table. One of the following values can be returned:
    
TBLSTAT_COMPLETE 
  
> No operations are in progress.
    
TBLSTAT_QCHANGED 
  
> The contents of the table have expectantly changed. This status value is not returned for changes that result from sort or restriction operations.
    
TBLSTAT_RESTRICT_ERROR 
  
> An error occurred during an [IMAPITable::Restrict](imapitable-restrict.md) operation. 
    
TBLSTAT_RESTRICTING 
  
> An **IMAPITable::Restrict** operation is in progress. 
    
TBLSTAT_SETCOL_ERROR 
  
> An error occurred during an [IMAPITable::SetColumns](imapitable-setcolumns.md) operation. 
    
TBLSTAT_SETTING_COLS 
  
> An **IMAPITable::SetColumns** operation is in progress. 
    
TBLSTAT_SORT_ERROR 
  
> An error occurred during an [IMAPITable::SortTable](imapitable-sorttable.md) operation. 
    
TBLSTAT_SORTING 
  
> An **IMAPITable::SortTable** operation is in progress. 
    
 _lpulTableType_
  
> [out] Pointer to a value that indicates the table's type. One of the following three table types can be returned:
    
TBLTYPE_DYNAMIC 
  
> The table's contents are dynamic; the rows and column values can change as the underlying data changes.
    
TBLTYPE_KEYSET 
  
> The rows within the table are fixed, but the values of the columns within these rows are dynamic and can change as the underlying data changes.
    
TBLTYPE_SNAPSHOT 
  
> The table is static, and its contents do not change when the underlying data changes.
    
## Return value

S_OK 
  
> The table's status was successfully returned.
    
## Remarks

The **IMAPTable::GetStatus** method retrieves information about a table's type and current status. 
  
## Notes to callers

You can use **GetStatus** in conjunction with three other **IMAPITable** methods to monitor the status of those operations and determine the effect on the table. Call **GetStatus** after making one of the following **IMAPITable** calls: 
  
- [IMAPITable::Restrict](imapitable-restrict.md) to set a restriction. 
    
- [IMAPITable::SortTable](imapitable-sorttable.md) to establish a sort order. 
    
- [IMAPITable::SetColumns](imapitable-setcolumns.md) to define a column set. 
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::GetStatus  <br/> |MFCMAPI uses the **IMAPITable::GetStatus** method to report the status of a table.  <br/> |
   
## See also



[IMAPITable::Restrict](imapitable-restrict.md)
  
[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[IMAPITable::SortTable](imapitable-sorttable.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

