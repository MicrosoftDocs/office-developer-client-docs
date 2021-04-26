---
title: "ACCT_BIN"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 5b57296c-61d7-e517-7ab7-44a9cc1f7ffc
description: "A variable of this data type holds a binary value."
---

# ACCT_BIN

A variable of this data type holds a binary value.
  
## Quick info

```cpp
typedef struct { 
    DWORD cb; 
    BYTE * pb; 
} ACCT_BIN; 

```

## Members

_cb_
  
> Number of bytes that  _pb_ points to. 
    
_pb_
  
> Pointer to binary information.
    

