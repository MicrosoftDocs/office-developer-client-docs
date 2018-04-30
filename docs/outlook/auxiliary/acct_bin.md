---
title: "ACCT_BIN"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5b57296c-61d7-e517-7ab7-44a9cc1f7ffc
description: "A variable of this data type holds a binary value."
---

# ACCT_BIN

A variable of this data type holds a binary value.
  
## Quick Info

```
typedef struct { 
    DWORDcb; 
    BYTE * pb; 
} ACCT_BIN; 

```

## Members

 _cb_
  
> Number of bytes that  _pb_ points to. 
    
 _pb_
  
> Pointer to binary information.
    

