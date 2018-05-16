---
title: "IExchangeModifyTableGetTable"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IExchangeModifyTable.GetTable
api_type:
- COM
ms.assetid: 97df32c4-07c6-41f1-84e7-c6e87d396e34
description: "Last modified: March 09, 2015"
---

# IExchangeModifyTable::GetTable

  
  
**Applies to**: Outlook 
  
Returns a pointer to an interface for a MAPI table object.
  
```
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
    
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|RulesDlg.cpp  <br/> |CRulesDlg::OnRefreshView  <br/> |MFCMAPI uses the **IExchangeModifyTable::GetTable** method to get a table of rules.  <br/> |
   
## See also

#### Reference

[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

