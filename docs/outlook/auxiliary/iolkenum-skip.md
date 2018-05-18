---
title: "IOlkEnumSkip"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: e83e409c-f201-df9d-5e30-879adf15318d
description: "Skips a specified number of accounts in the enumerator."
---

# IOlkEnum::Skip

Skips a specified number of accounts in the enumerator.
  
## Quick info

See [IOlkEnum](iolkenum.md).
  
```
HRESULT IOlkEnum::Skip(  
    DWORD cSkip 
);
```

## Parameters

 _cSkip_
  
> [in] The number of accounts to be skipped.
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## See also



[IOlkEnum::GetCount](iolkenum-getcount.md)
  
[IOlkEnum::GetNext](iolkenum-getnext.md)
  
[IOlkEnum::Reset](iolkenum-reset.md)

