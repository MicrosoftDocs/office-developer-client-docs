---
title: "IMAPITableQueryPosition"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.QueryPosition
api_type:
- COM
ms.assetid: 510b2e21-ba27-47dd-87cb-2a549e31fa28
description: "Last modified: July 23, 2011"
---

# IMAPITable::QueryPosition

  
  
**Applies to**: Outlook 
  
Retrieves the current table row position of the cursor, based on a fractional value.
  
```
HRESULT QueryPosition(
ULONG FAR * lpulRow,
ULONG FAR * lpulNumerator,
ULONG FAR * lpulDenominator
);
```

## Parameters

 _lpulRow_
  
> [out] Pointer to the number of the current row. The row number is zero-based; the first row in the table is zero. 
    
 _lpulNumerator_
  
> [out] Pointer to the numerator for the fraction identifying the table position.
    
 _lpulDenominator_
  
> [out] Pointer to the denominator for the fraction identifying the table position. The  _lpulDenominator_ parameter cannot be zero. 
    
## Return value

S_OK 
  
> The method returned valid values in  _lpulRow_,  _lpulNumerator_, and  _lpulDenominator_.
    
## Remarks

The **IMAPITable::QueryPosition** method determines the current row position and returns both the number of the current row and a fractional value indicating its relative position to the end of the table. MAPI defines the current row as the next row to be read. 
  
## Notes to Implementers

You do not need to return the exact number of rows in the table for the  _lpulDenominator_ parameter; it can be an approximation. 
  
If you cannot determine the current row, return a value of 0xFFFFFFFF in  _lpulRow_.
  
## Notes to Callers

You can use **QueryPosition** to position a scroll box in a scroll bar. For example, in a table containing 100 rows, if **QueryPosition** returns a value of 75 in the  _lpulNumerator_ parameter, 100 in the  _lpulDenominator_ parameter, and 75 in the  _lpulRow_ parameter, you can position the scroll box 3/4 of the way across the scroll bar. 
  
Do not rely on the value in  _lpulDenominator_ being the number of rows in the table. **QueryPosition** cannot always identify the exact row that the cursor is positioned on. 
  
A call to **QueryPosition** might involve large amounts of memory, particularly for large categorized tables. If the  _lpulRow_ parameter is set to 0xFFFFFFFF, too much memory was required for **QueryPosition** to determine the current row. Call the [IMAPITable::SeekRowApprox](imapitable-seekrowapprox.md) method to position the table to the row identified by the  _lpulNumerator_ and  _lpulDenominator_ parameters. However, do not always expect **SeekRowApprox** to establish as the current position the same row **QueryPosition** would have if memory had not been a factor. 
  
## See also

#### Reference

[IMAPITable::SeekRowApprox](imapitable-seekrowapprox.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

