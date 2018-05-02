---
title: "IMAPITableGetCollapseState"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.GetCollapseState
api_type:
- COM
ms.assetid: fd4ea496-4c83-49cd-854e-f373cc1ed2af
description: "Last modified: July 23, 2011"
---

# IMAPITable::GetCollapseState

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Returns the data that is needed to rebuild the current collapsed or expanded state of a categorized table.
  
```
HRESULT GetCollapseState(
ULONG ulFlags,
ULONG cbInstanceKey,
LPBYTE lpbInstanceKey,
ULONG FAR * lpcbCollapseState,
LPBYTE FAR * lppbCollapseState
);
```

## Parameters

 _ulFlags_
  
> Reserved; must be zero.
    
 _cbInstanceKey_
  
> [in] The count of bytes in the instance key pointed to by the  _lpbInstanceKey_ parameter. 
    
 _lpbInstanceKey_
  
> [in] A pointer to the **PR_INSTANCE_KEY** ( [PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) property of the row at which the current collapsed or expanded state should be rebuilt. The  _lpbInstanceKey_ parameter cannot be NULL. 
    
 _lpcbCollapseState_
  
> [out] A pointer to the count of structures pointed to by the  _lppbCollapseState_ parameter. 
    
 _lppbCollapseState_
  
> [out] A pointer to a pointer to structures that contain data that describes the current table view.
    
## Return value

S_OK 
  
> The state for the categorized table was successfully saved.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
MAPI_E_NO_SUPPORT 
  
> The table does not support categorization and expanded and collapsed views.
    
## Remarks

The **IMAPITable::GetCollapseState** method works with the [IMAPITable::SetCollapseState](imapitable-setcollapsestate.md) method to change the user's view of a categorized table. **GetCollapseState** saves the data that is needed for **SetCollapseState** to use to rebuild the appropriate views of the categories of a categorized table. Service providers determine the data to be saved. However, most service providers implementing **GetCollapseState** save the following: 
  
- The sort keys (standard columns and category columns).
    
- Information about the row that the instance key represents.
    
- Information to restore the collapsed and expanded categories of the table.
    
For more information about categorized tables, see [Sorting and Categorization](sorting-and-categorization.md).
  
## Notes to Implementers

Store the current state of all nodes of a table in the  _lppbCollapseState_ parameter. 
  
## Notes to Callers

Always call **GetCollapseState** before you call **SetCollapseState**. 
  
## See also

#### Reference

[IMAPITable::SetCollapseState](imapitable-setcollapsestate.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

