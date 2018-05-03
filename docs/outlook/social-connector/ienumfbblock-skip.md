---
title: "IEnumFBBlockSkip"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 70fbdb41-46ea-d016-25a2-37e94962095d
description: "Skips a specified number of blocks of free/busy data."
---

# IEnumFBBlock::Skip

Skips a specified number of blocks of free/busy data.
  
## Quick Info

See [IEnumFBBlock](ienumfbblock.md).
  
```
HRESULT Skip(  
    LONG celt 
);
```

## Parameters

 _celt_
  
>  [in] The number of free/busy blocks to skip. 
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## See also

#### Concepts

[IEnumFBBlock::Clone](ienumfbblock-clone.md)
  
[IEnumFBBlock::Next](ienumfbblock-next.md)
  
[IEnumFBBlock::Reset](ienumfbblock-reset.md)
  
[IEnumFBBlock::Restrict](ienumfbblock-restrict.md)

