---
title: "ScCreateConversationIndex"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ScCreateConversationIndex
api_type:
- COM
ms.assetid: 3ccfc15d-f3c6-4c7b-b1cc-855af66036de
description: "Last modified: March 09, 2015"
---

# ScCreateConversationIndex

  
  
**Applies to**: Outlook 
  
Indicates where in a message thread a message belongs. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScCreateConversationIndex(
  ULONG cbParent,
  LPBYTE lpbParent,
  ULONG FAR* lpcbIndex,
  LPBYTE FAR * lppbIndex
);
```

## Parameters

 _cbParent_
  
> [in] Count of bytes in the parent conversation index.
    
 _lpbParent_
  
> [in] Pointer to bytes in the parent conversation index. This may be NULL if  _cbParent_ is zero. 
    
 _lpcbIndex_
  
> [out] Pointer to the count of bytes in the new conversation index returned by the call. 
    
 _lppbIndex_
  
> [out] Pointer to a pointer to the new conversation index returned by the call.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    

