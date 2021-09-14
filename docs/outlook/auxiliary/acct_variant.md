---
title: "ACCT_VARIANT"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 4664df83-cf81-36d4-189d-4a09be371638
description: "A variable of this data type holds the value of a property, which is of a variant data type."
---

# ACCT_VARIANT

A variable of this data type holds the value of a property, which is of a variant data type.
  
## Quick info

```cpp
typedef struct 
    { 
        DWORD dwType; 
        union  
            { 
            DWORD dw; 
            WCHAR *pwsz; 
            ACCT_BIN bin; 
            } Val; 
    } ACCT_VARIANT; 

```

## Members

_dwType_
  
> Type of variant:
    
    - PT_LONG
    
    - PT_UNICODE
    
    - PT_BINARY
    
_dw_
  
> DWORD value of variant.
    
_pwsz_
  
> String value of variant.
    
_bin_
  
> Binary value of the variant.
    

