---
title: "MapStorageSCode"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MapStorageSCode
api_type:
- COM
ms.assetid: f686a2bc-aba5-4ea3-9963-76d0e96eab50
description: "Last modified: March 09, 2015"
---

# MapStorageSCode

  
  
**Applies to**: Outlook 
  
Maps an SCODE return value from an OLE storage object to an HRESULT type. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE MapStorageSCode(
  SCODE StgSCode
);
```

## Parameters

 _StgSCode_
  
> [in] MAPI SCODE return value from an OLE storage object to be mapped to a HRESULT value.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value.
    
MAPI_E_CALL_FAILED 
  
> The function cannot find a matching value.
    
## Remarks

MAPI provides the **MapStorageSCode** function for the internal use of MAPI components that base their message implementations on the message DLL. Because these components open OLE storage themselves, they must be able to map error values returned for problems with OLE storage to an HRESULT value. 
  
For more information, see [Structured Storage](structured-storage-in-mapi.md). 
  

