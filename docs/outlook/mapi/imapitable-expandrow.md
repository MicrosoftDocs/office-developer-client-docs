---
title: "IMAPITableExpandRow"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.ExpandRow
api_type:
- COM
ms.assetid: b96dd8f6-e648-4014-8a1d-ae1da771c439
description: "Last modified: March 09, 2015"
---

# IMAPITable::ExpandRow

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Expands a collapsed table category, adding the leaf or lower-level heading rows belonging to the category to the table view.
  
```cpp
HRESULT ExpandRow(
ULONG cbInstanceKey,
LPBYTE pbInstanceKey,
ULONG ulRowCount,
ULONG ulFlags,
LPSRowSet FAR * lppRows,
ULONG FAR * lpulMoreRows
);
```

## Parameters

 _cbInstanceKey_
  
> [in] The count of bytes in the PR_INSTANCE_KEY property pointed to by the  _pbInstanceKey_ parameter. 
    
 _pbInstanceKey_
  
> [in] A pointer to the **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) property that identifies the heading row for the category. 
    
 _ulRowCount_
  
> [in] The maximum number of rows to return in the _lppRows_ parameter. 
    
 _ulFlags_
  
> Reserved; must be zero.
    
 _lppRows_
  
> [out] A pointer to an [SRowSet](srowset.md) structure receiving the first (up to  _ulRowCount_) rows that have been inserted into the table view as a result of the expansion. These rows are inserted after the heading row identified by the  _pbInstanceKey_ parameter. The  _lppRows_ parameter can be NULL if the _ulRowCount_ parameter is zero. 
    
 _lpulMoreRows_
  
> [out] A pointer to the total number of rows that were added to the table view.
    
## Return value

S_OK 
  
> The category was expanded successfully.
    
MAPI_E_NOT_FOUND 
  
> The row identified by the  _pbInstanceKey_ parameter does not exist. 
    
## Remarks

The **IMAPITable::ExpandRow** method expands a collapsed table category, adding the leaf or lower-level heading rows that belong to the category to the table view. A limit to the number of rows to be returned in the _lppRows_ parameter can be specified in the _ulRowCount_ parameter. When  _ulRowCount_ is set to a value greater than zero and one or more rows are returned in the row set pointed to by  _lppRows_, the position of the bookmark BOOKMARK_CURRENT is moved to the row immediately following the last row in the row set.
  
When  _ulRowCount_ is set to zero, requesting that zero leaf or lower-level heading rows be added to the category, or zero rows are returned because there are no leaf or lower-level heading rows in the category, the position of BOOKMARK_CURRENT is set to the row following the row identified by  _pbInstanceKey_. 
  
## Notes to implementers

Do not generate notifications on rows that are added to a table view due to category expansion.
  
## Notes to callers

The number of rows in the row set pointed to by the  _lppRows_ parameter might not equal the number of rows that were actually added to the table, the entire set of leaf or lower-level heading rows for the category. Errors can occur, such as insufficient memory, or the number of rows in the category exceeding the number specified in  _ulRowCount_ parameter. In either case, BOOKMARK_CURRENT will be positioned at the last row returned. To immediately retrieve the rest of the rows in the category, call [IMAPITable::QueryRows](imapitable-queryrows.md).
  
Do not expect to receive a table notification when a category changes its state. You can maintain a local cache of rows that can be updated with every **ExpandRow** or **CollapseRow** call. 
  
For more information about categorized tables, see [Sorting and Categorization](sorting-and-categorization.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::DoExpandCollapse  <br/> |MFCMAPI uses the **IMAPITable::ExpandRow** method to expand a collapsed table category.  <br/> |
   
## See also



[IMAPITable::CollapseRow](imapitable-collapserow.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

