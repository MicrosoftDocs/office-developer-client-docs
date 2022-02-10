---
title: "IMAPITableCollapseRow"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.CollapseRow
api_type:
- COM
ms.assetid: 1a23e555-be26-43fb-a715-cfc4ffa623cd
description: "Last modified: March 09, 2015"
---

# IMAPITable::CollapseRow

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Collapses an expanded table category, removing any lower-level headings and leaf rows belonging to the category from the table view.
  
```cpp
HRESULT CollapseRow(
ULONG cbInstanceKey,
LPBYTE pbInstanceKey,
ULONG ulFlags,
ULONG FAR * lpulRowCount
);
```

## Parameters

 _cbInstanceKey_
  
> [in] The count of bytes in the PR_INSTANCE_KEY property pointed to by the  _pbInstanceKey_ parameter. 
    
 _pbInstanceKey_
  
> [in] A pointer to the **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) property that identifies the heading row for the category. 
    
 _ulFlags_
  
> Reserved; must be zero.
    
 _lpulRowCount_
  
> [out] A pointer to the total number of rows that are being removed from the table view.
    
## Return value

S_OK 
  
> The collapse operation has succeeded.
    
MAPI_E_NOT_FOUND 
  
> The row identified by the  _pbInstanceKey_ parameter does not exist. 
    
MAPI_E_INVALID_ENTRYID 
  
> The row identified by the  _pbInstanceKey_ parameter does not exist. This error is an alternative to MAPI_E_NOT_FOUND; service providers can return either one. 
    
## Remarks

The **IMAPITable::CollapseRow** method collapses a table category and removes it from the table view. The rows are collapsed starting at the row identified by the **PR_INSTANCE_KEY** property pointed to by the  _pbInstanceKey_ parameter. The number of rows that are removed from the view is returned in the contents of the  _lpulRowCount_ parameter. 
  
Notifications are never generated for table rows that are removed from a view as the result of a collapse operation. 
  
When a row that is defined by a bookmark is collapsed out of view, the bookmark is moved to point to the next visible row. 
  
For more information about categorized tables, see [Sorting and Categorization](sorting-and-categorization.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::DoExpandCollapse  <br/> |MFCMAPI uses the **IMAPITable::CollapseRow** method to collapse a table category. |
   
## See also



[IMAPITable::ExpandRow](imapitable-expandrow.md)
  
[IMAPITable::GetCollapseState](imapitable-getcollapsestate.md)
  
[IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
  
[IMAPITable::SetCollapseState](imapitable-setcollapsestate.md)
  
[IMAPITable::SortTable](imapitable-sorttable.md)
  
[SSortOrderSet](ssortorderset.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

