---
title: "SCODE"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.HRESULT
api_type:
- COM
ms.assetid: 2348cce1-07c3-49ed-ae03-79e477d3c6c2
description: "Last modified: July 23, 2011"
---

# SCODE

**Applies to**: Outlook 2013 | Outlook 2016 
  
A 32-bit status value that is used to describe an error or warning. 
  
```cpp
typedef ULONG SCODE;

```

## Remarks

The **SCODE** data type is the same as the [HRESULT](hresult.md) data type. 
  
An **SCODE** value is divided into four fields: 
  
- A single-bit severity code which is set to 0 to indicate success and 1 to indicate failure.
    
- An 11-bit reserved field
    
- A 4-bit facility code which indicates the area responsible for the error or warning.
    
- A 16-bit error or warning code which describes the problem that is causing the error or warning.
    
Many of the MAPI functions and methods return **SCODE** values defined as **HRESULT** data types as do the OLE methods and functions. OLE defines several macros that can be used to convert between an **SCODE** and an **HRESULT**.
  
> [!NOTE]
> In 64-bit MAPI, **SCODE** is still a 32-bit value. 
  
For more information about how MAPI uses the **SCODE** data type, see [Error Handling](error-handling-in-mapi.md). For more information about OLE and the **SCODE** data type, see the  *OLE Programmer's Reference*  . 
  
## See also



[HRESULT](hresult.md)


[MAPI Data Types](mapi-data-types.md)

