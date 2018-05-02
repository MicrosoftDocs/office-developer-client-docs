---
title: "IOlkAccountSetProp"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 883b1c5d-47dd-a006-b5f1-130691bdd019
description: "Sets the value of the specified account property."
 
 
---

# IOlkAccount::SetProp

Sets the value of the specified account property.
  
## Quick Info

See [IOlkAccount](iolkaccount.md).
  
```
HRESULT IOlkAccount::SetProp(  
    DWORD dwProp, 
    ACCT_VARIANT *pVar 
);
```

## Parameters

 _dwProp_
  
> [in] The property tag of the account property to set.
    
 _pVar_
  
> [in] The value of the specified property.
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The method call was successful.  <br/> |
|E_INVALIDARG  <br/> |An invalid property tag was specified.  <br/> |
   
## Remarks

Use [IOlkAccount::SaveChanges](iolkaccount-savechanges.md) to save changes to the value of account properties. 
  
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkAccount::GetProp](iolkaccount-getprop.md)

