---
title: "ROWLIST"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ROWLIST
api_type:
- COM
ms.assetid: ce0be0d5-4962-4d53-828f-c93d1c5aae32
description: "Last modified: March 09, 2015"
---

# ROWLIST

  
  
**Applies to**: Outlook 
  
Contains an array of [ROWENTRY](rowentry.md) structures representing rows and the operations that are performed on those rows in a table through the [IExchangeModifyTable](iexchangemodifytableiunknown.md) interface. 
  
```cpp
typedef struct
{
  ULONG     cEntries;
  ROWENTRY  aEntries[MAPI_DIM];
}  ROWLIST, FAR * LPROWLIST;

```

## Members

 **cEntries**
  
> Count of entries in the array specified by the **aEntries** member. 
    
 **aEntries[MAPI_DIM]**
  
> Array of **ROWENTRY** structures that contains the rows and the operations that are performed on those rows in the table. 
    
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|RulesDlg.cpp  <br/> |CRulesDlg::GetSelectedItems  <br/> |Used to build a list of selected rules for subsequent **ModifyTable** actions.  <br/> |
   
## See also



[ROWENTRY](rowentry.md)
  
[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)


[MAPI Structures](mapi-structures.md)

