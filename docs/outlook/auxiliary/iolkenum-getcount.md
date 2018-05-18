---
title: "IOlkEnumGetCount"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: dd7a7e62-4cf2-bdd3-8a00-4fff5ac575d3
description: "Gets the number of accounts in the enumerator."
---

# IOlkEnum::GetCount

Gets the number of accounts in the enumerator.
  
## Quick info

See [IOlkEnum](iolkenum.md).
  
```
HRESULT IOlkEnum::GetCount ( 
    DWORD *pulCount 
);

```

## Parameters

 _pulCount_
  
> [out] A pointer to the number of objects being enumerated.
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## See also



[IOlkEnum::GetNext](iolkenum-getnext.md)
  
[IOlkEnum::Reset](iolkenum-reset.md)
  
[IOlkEnum::Skip](iolkenum-skip.md)

