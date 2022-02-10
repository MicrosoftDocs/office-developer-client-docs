---
title: "IExchangeModifyTableGetTable"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IExchangeModifyTable.GetTable
api_type:
- COM
ms.assetid: 97df32c4-07c6-41f1-84e7-c6e87d396e34
description: "Last modified: March 09, 2015"
---

# IExchangeModifyTable::GetTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a pointer to an interface for a MAPI table object.
  
```cpp
HRESULT GetTable( 
  ULONG ulFlags, 
  LPMAPITABLE FAR * lppTable 
); 

```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be 0 (zero).
    
ACLTABLE_FREEBUSY
  
> Sets new rights.
    
frightsFreeBusyDetailed
  
> When ACLTABLE_FREEBUSY is passed, provides a detailed display of new free/busy rights.
    
frightsFreeBusySimple
  
> When ACLTABLE_FREEBUSY is passed, provides a simple display of new free/busy rights.
    
 _lppTable_
  
> [out] Points to a [IMAPITable : IUnknown](imapitableiunknown.md) interface containing the table object. 
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|RulesDlg.cpp  <br/> |CRulesDlg::OnRefreshView  <br/> |MFCMAPI uses the **IExchangeModifyTable::GetTable** method to get a table of rules. |
   
## See also



[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

