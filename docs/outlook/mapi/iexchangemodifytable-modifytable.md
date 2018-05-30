---
title: "IExchangeModifyTableModifyTable"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IExchangeModifyTable.ModifyTable
api_type:
- COM
ms.assetid: b9a745cc-260d-4a1c-896e-6a038ab3cfb9
description: "Last modified: March 09, 2015"
---

# IExchangeModifyTable::ModifyTable

  
  
**Applies to**: Outlook 
  
Updates a MAPI table object.
  
```cpp
HRESULT ModifyTable( 
  ULONG ulFlags, 
  LPROWLIST lpMods 
); 

```

## Parameters

 _ulFlags_
  
> [in] Use one of the following values: 
    
0 (zero)
  
> Use the value of the **ulRowFlags** member of the [ROWENTRY](rowentry.md) structure. 
    
ACLTABLE_FREEBUSY
  
> Sets new rights.
    
frightsFreeBusyDetailed
  
> When ACLTABLE_FREEBUSY is passed, provides a detailed display of new free/busy rights.
    
frightsFreeBusySimple
  
> When ACLTABLE_FREEBUSY is passed, provides a simple display of new free/busy rights.
    
ROWLIST_REPLACE
  
> Replace all the rows in the table.
    
 _lpMods_
  
> [in] Points to a [ROWLIST](rowlist.md) structure containing the properties for the table object. 
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|RulesDlg.cpp  <br/> |CRulesDlg::OnModifySelectedItem  <br/> |MFCMAPI uses the **IExchangeModifyTable::ModifyTable** method to write a modified rule back to the table of rules.  <br/> |
   
## See also



[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)
  
[ROWENTRY](rowentry.md)
  
[ROWLIST](rowlist.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

