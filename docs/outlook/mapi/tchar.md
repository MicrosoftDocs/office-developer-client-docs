---
title: "TCHAR"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.TCHAR
api_type:
- COM
ms.assetid: 7a92060b-4c30-4eba-993f-36f5f9231a4b
description: "Last modified: July 23, 2011"
---

# TCHAR

  
  
**Applies to**: Outlook 
  
A Win32 character string that can be used to describe ANSI, DBCS, or Unicode strings. For ANSI and DBCS platforms, TCHAR is defined as follows:
  
```
typedef char TCHAR;

```

## Remarks

For Unicode platforms, TCHAR is defined as synonymous with the WCHAR type. 
  
MAPI clients can use the TCHAR data type to represent a string of either the WCHAR or char type. Be sure to define the symbolic constant UNICODE and limit the platform when it is required. MAPI will interpret the platform information and internally translate TCHAR to the appropriate string. The MAPI property type, PT_TSTRING, works just like the TCHAR data type. When the platform supports Unicode, properties of type PT_TSTRING are assigned the type PT_UNICODE at compile time. When the platform does not support Unicode, these properties are assigned the type PT_STRING8.
  
For more information about this functionality, see [Character Sets](mapi-character-sets.md) and [List of Property Types](property-types.md). 
  
## See also

#### Concepts

[MAPI Data Types](mapi-data-types.md)

