---
title: "HRESULT"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.HRESULT
api_type:
- COM
ms.assetid: b248ed11-3d8a-4d4c-9b84-fa5bee7979c7
description: "Last modified: July 23, 2011"
---

# HRESULT

**Applies to**: Outlook 2013 | Outlook 2016
  
A 32-bit value that is used to describe an error or warning.
  
```cpp
typedef LONG HRESULT;
```

## Remarks

The **HRESULT** data type is the same as the [SCODE](scode.md) data type.

An **HRESULT** value consists of the following fields:
  
- A 1-bit code indicating severity, where zero represents success and 1 represents failure.

- A 4-bit reserved value.

- An 11-bit code indicating responsibility for the error or warning, also known as a facility code.

- A 16-bit code describing the error or warning.

Most MAPI interface methods and functions return **HRESULT** values to provide detailed cause formation. **HRESULT** values are also used widely in OLE interface methods. OLE provides several macros for converting between **HRESULT** values and **SCODE** values, another common data type for error handling.
  
> [!NOTE]
> In 64-bit MAPI, **HRESULT** is still a 32-bit value.
  
For information about the OLE use of **HRESULT** values, see the  *OLE Programmer's Reference*. For more information about the use of these values in MAPI, see [Error Handling](error-handling-in-mapi.md) and any of the following interface methods:
  
[IABLogon::GetLastError](iablogon-getlasterror.md)
  
[IMAPISupport::GetLastError](imapisupport-getlasterror.md)
  
[IMAPIControl::GetLastError](imapicontrol-getlasterror.md)
  
[IMAPITable::GetLastError](imapitable-getlasterror.md)
  
[IMAPIProp::GetLastError](imapiprop-getlasterror.md)
  
[IMAPIViewAdviseSink::OnPrint](imapiviewadvisesink-onprint.md)
  
## See also

[SCODE](scode.md)
[MAPI Data Types](mapi-data-types.md)
