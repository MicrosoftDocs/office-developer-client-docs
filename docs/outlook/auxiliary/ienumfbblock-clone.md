---
title: "IEnumFBBlockClone"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 5af36a87-e782-df63-4190-a608758fef50
description: "Creates a copy of the enumerator, using the same time restriction but setting the cursor to the beginning of the enumerator."
---

# IEnumFBBlock::Clone

Creates a copy of the enumerator, using the same time restriction but setting the cursor to the beginning of the enumerator.
  
## Quick info

See [IEnumFBBlock](ienumfbblock.md).
  
```cpp
HRESULT Clone(  
     IEnumFBBlock **ppclone 
); 
```

## Parameters

_ppclone_
  
> [out] A pointer to pointer to the copy of [IEnumFBBlock](ienumfbblock.md) interface. 
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_OUTOFMEMORY  <br/> |There is insufficient memory for making the copy.  <br/> |
   
## See also

- [Constants (Free/busy API)](constants-free-busy-api.md)
- [IEnumFBBlock::Next](ienumfbblock-next.md)  
- [IEnumFBBlock::Reset](ienumfbblock-reset.md)  
- [IEnumFBBlock::Restrict](ienumfbblock-restrict.md)  
- [IEnumFBBlock::Skip](ienumfbblock-skip.md)

