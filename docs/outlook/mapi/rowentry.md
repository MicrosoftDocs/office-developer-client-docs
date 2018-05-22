---
title: "ROWENTRY"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ROWENTRY
api_type:
- COM
ms.assetid: bd6c0d8e-68cc-4d60-9029-13ed81c816cd
description: "Last modified: March 09, 2015"
---

# ROWENTRY

**Applies to**: Outlook 
  
Contains a row and the operation that is performed on that row in a table through the [IExchangeModifyTable](iexchangemodifytableiunknown.md) interface. 
  
```cpp
typedef struct
{
  ULONG         ulRowFlags;
  ULONG         cValues;
  LPSPropValue  rgPropVals;
}  ROWENTRY, FAR * LPROWENTRY;
```

## Members

**ulRowFlags**
  
> One of the following operations to be performed on the data: 
    
  - ROW_ADD: Add the data to the table as a new row.
      
  - ROW_MODIFY: Modify this row in the table.
      
  - ROW_REMOVE: Remove this row from the table.
      
  - ROW_EMPTY: Do not add the row data to the table. (The row is empty.)
    
**cValues**
  
> The number of property values in **rgPropvals**.
    
**rgPropVals**
  
> An array of [SPropValue](spropvalue.md) structures representing the columns values to be inserted into the table. 
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|RulesDlg.cpp  <br/> |CRulesDlg::GetSelectedItems  <br/> |Used to build a list of selected rules for subsequent **ModifyTable** actions.  <br/> |
   
## See also
  
- [IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)
- [MAPI Structures](mapi-structures.md)

