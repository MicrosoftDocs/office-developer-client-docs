---
title: "IEnumFBBlockSkip"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 70fbdb41-46ea-d016-25a2-37e94962095d
description: "Skips a specified number of blocks of free/busy data."
---

# IEnumFBBlock::Skip

Skips a specified number of blocks of free/busy data.
  
## Quick info

See [IEnumFBBlock](ienumfbblock.md).
  
```cpp
HRESULT Skip(  
    LONG celt 
);
```

## Parameters

_celt_
  
> [in] The number of free/busy blocks to skip. 
    
## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## See also

- [IEnumFBBlock::Clone](ienumfbblock-clone.md)  
- [IEnumFBBlock::Next](ienumfbblock-next.md)  
- [IEnumFBBlock::Reset](ienumfbblock-reset.md)  
- [IEnumFBBlock::Restrict](ienumfbblock-restrict.md)

