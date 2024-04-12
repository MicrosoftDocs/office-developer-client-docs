---
title: "IMAPITableSeekRowApprox"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.SeekRowApprox
api_type:
- COM
ms.assetid: ce5e8c43-06af-4afc-9138-5cc51d8fc401
---

# IMAPITable::SeekRowApprox

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Moves the cursor to an approximate fractional position in the table. 
  
```cpp
HRESULT SeekRowApprox(
ULONG ulNumerator,
ULONG ulDenominator
);
```

## Parameters

 _ulNumerator_
  
> [in] Pointer to the numerator of the fraction representing the table position. If the  _ulNumerator_ parameter is zero, the cursor is positioned at the beginning of the table regardless of the denominator value. If  _ulNumerator_ is equal to the  _ulDenominator_ parameter, the cursor is positioned after the last table row. 
    
 _ulDenominator_
  
> [in] Pointer to the denominator of the fraction representing the table position. The  _ulDenominator_ parameter cannot be zero. 
    
## Return value

S_OK 
  
> The seek operation was successful.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the row seeking operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
## Remarks

The cursor position in a table after a call to the **IMAPITable::SeekRowApprox** method is heuristically the fraction and might not be exact. For example, certain providers might implement a table on top of a binary tree, treating the table's halfway point as the top of the tree for performance reasons. If the tree is not balanced, then the halfway point used might not be exactly halfway through the table. 
  
## Notes to callers

Call **SeekRowApprox** to provide the data for a scroll bar implementation. For example, if the user positions the scroll box 2/3 down the scroll bar, you can model that action by calling **SeekRowApprox** and passing in an equivalent fractional value using  _ulNumerator_ and  _ulDenominator_. The **SeekRowApprox** search is always absolute from the beginning of the table. To move to the end of the table, the values in  _ulNumerator_ and  _ulDenominator_ must be the same. 
  
Use whatever number scheme is appropriate. That is, to seek to a position halfway through the table, you can specify 1/2, 10/20, or 50/100. 
  
## See also



[IMAPITable : IUnknown](imapitableiunknown.md)

