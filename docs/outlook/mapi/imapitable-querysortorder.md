---
title: "IMAPITableQuerySortOrder"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.QuerySortOrder
api_type:
- COM
ms.assetid: 7b4ca523-0703-417c-8586-c4324c200020
---

# IMAPITable::QuerySortOrder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the current sort order for a table.
  
```cpp
HRESULT QuerySortOrder(
LPSSortOrderSet FAR * lppSortCriteria
);
```

## Parameters

 _lppSortCriteria_
  
> [out] Pointer to a pointer to the [SSortOrderSet](ssortorderset.md) structure holding the current sort order. 
    
## Return value

S_OK 
  
> The current sort order was successfully returned.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the sort order retrieval operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
## Remarks

The **IMAPITable::QuerySortOrder** method retrieves the current sort order for a table. Sort orders are described with an [SSortOrderSet](ssortorderset.md) structure. 
  
- The **cSorts** member of the **SSortOrderSet** structure can be set to zero if: 
    
- The table is unsorted.
    
- There is no information about how the table is sorted.
    
- The **SSortOrderSet** structure is not appropriate for describing the sort order. 
    
## Notes to implementers

If a call is made to your [IMAPITable::SortTable](imapitable-sorttable.md) method with an **SSortOrderSet** structure containing zero columns in the sort key, remove the current sort order and apply the default order, if there is one. In subsequent calls to **QuerySortOrder**, you can choose whether to return zero or more columns for the sort key. You can return more columns than are in the present view.
  
For more information about sorting, see [Sorting and Categorization](sorting-and-categorization.md).
  
## See also



[IMAPITable::SortTable](imapitable-sorttable.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SSortOrderSet](ssortorderset.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

