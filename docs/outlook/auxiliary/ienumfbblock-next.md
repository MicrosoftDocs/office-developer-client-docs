---
title: "IEnumFBBlockNext"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 9b46358c-bcab-f097-8746-fabfd4722b3c
description: "Gets the next specified number of blocks of free/busy data in an enumeration."
---

# IEnumFBBlock::Next

Gets the next specified number of blocks of free/busy data in an enumeration.
  
## Quick info

See [IEnumFBBlock](ienumfbblock.md).
  
```cpp
HRESULT Next(  
        LONG celt,
        FBBlock_1 *pblk,
        LONG *pcfetch
);
```

## Parameters

_celt_
  
> [in] The number of free/busy data blocks in *pblk*  to retrieve.

_pblk_
  
> [in] A pointer to an array of free/busy blocks. The array is allocated a size of *celt*. The requested free/busy blocks are returned in this array.

_pcfetch_
  
> [out] The number of free/busy blocks actually returned in *pblk*.

## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The requested number of blocks has been returned. |
|S_FALSE  <br/> |The requested number of blocks has not been returned. |

## See also

- [Constants (Free/busy API)](constants-free-busy-api.md)  
- [FBBlock_1](fbblock_1.md)  
- [IEnumFBBlock::Clone](ienumfbblock-clone.md)  
- [IEnumFBBlock::Reset](ienumfbblock-reset.md)  
- [IEnumFBBlock::Restrict](ienumfbblock-restrict.md)  
- [IEnumFBBlock::Skip](ienumfbblock-skip.md)
