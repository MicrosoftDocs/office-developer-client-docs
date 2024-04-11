---
title: "IMAPITableSetCollapseState"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.SetCollapseState
api_type:
- COM
ms.assetid: 31325e8f-1cf9-49b2-8118-953996b0037f
---

# IMAPITable::SetCollapseState

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Rebuilds the current expanded or collapsed state of a categorized table using data that was saved by a prior call to the [IMAPITable::GetCollapseState](imapitable-getcollapsestate.md) method. 
  
```cpp
HRESULT SetCollapseState(
ULONG ulFlags,
ULONG cbCollapseState,
LPBYTE pbCollapseState,
BOOKMARK FAR * lpbkLocation
);
```

## Parameters

 _ulFlags_
  
> Reserved; must be zero.
    
 _cbCollapseState_
  
> [in] Count of bytes in the structure pointed to by the  _pbCollapseState_ parameter. 
    
 _pbCollapseState_
  
> [in] Pointer to the structures containing the data needed to rebuild the table view.
    
 _lpbkLocation_
  
> [out] Pointer to a bookmark identifying the row in the table at which the collapsed or expanded state should be rebuilt. This bookmark and the instance key passed in the _lpbInstanceKey_ parameter in the call to [IMAPITable::GetCollapseState](imapitable-getcollapsestate.md) identify the same row. 
    
## Return value

S_OK 
  
> The state of the categorized table was successfully rebuilt.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
MAPI_E_UNABLE_TO_COMPLETE 
  
> The table could not finish rebuilding the collapsed or expanded view.
    
## Remarks

The **IMAPITable::SetCollapseState** method reestablishes the expanded or collapsed state of the table view. **SetCollapseState** and **GetCollapseState** work together as follows: 
  
1. When the state of a categorized table is about to change, [IMAPITable::GetCollapseState](imapitable-getcollapsestate.md) is called to save all of the data pertaining to the state prior to the change. 
    
2. To restore the view of the table to its saved state, **SetCollapseState** is called. The data saved by **GetCollapseState** is passed to **SetCollapseState**. **SetCollapseState** is able to use that data to restore the state. 
    
3. **SetCollapseState** returns as an output parameter a bookmark that identifies the same row as the instance key passed as input to **GetCollapseState**.
    
For more information about categorized tables, see [Sorting and Categorization](sorting-and-categorization.md). 
  
## Notes to implementers

You are responsible for verifying that the sort order and restrictions are exactly the same as they were at the time of the **GetCollapseState** call. If a change has been made, **SetCollapseState** should not be called because the results can be unpredictable. This can happen if, for example, a client calls **GetCollapseState** and then **SortTable** to change the sort key before calling **SetCollapseState**. To be safe, check that the saved data is still valid before proceeding with the restoration. 
  
## Notes to callers

To call **SetCollapseState**, you must have previously called **GetCollapseState**. The sort order establishing the categories should be the same for both methods. If the sort orders differ, the results of the **SetCollapseState** operation are unpredictable. 
  
## See also



[IMAPITable::CreateBookmark](imapitable-createbookmark.md)
  
[IMAPITable::FreeBookmark](imapitable-freebookmark.md)
  
[IMAPITable::GetCollapseState](imapitable-getcollapsestate.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

