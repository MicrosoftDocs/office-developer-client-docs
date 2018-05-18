---
title: "MSGCALLRELEASE"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MSGCALLRELEASE
api_type:
- COM
ms.assetid: 23c08597-41f0-4f48-a63e-79962fa812bc
description: "Last modified: March 09, 2015"
---

# MSGCALLRELEASE

  
  
**Applies to**: Outlook 
  
Defines a callback function that can free an **IStorage** interface after the final release of an **IMessage** object built on top of it with the [OpenIMsgOnIStg](openimsgonistg.md) function. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Defined function implemented by:  <br/> |Client applications and service providers  <br/> |
|Defined function called by:  <br/> |MAPI  <br/> |
   
```cpp
typedef void (STDAPICALLTYPE MSGCALLRELEASE)(
  ULONG  ulCallerData,
  LPMESSAGE  lpMessage );
```

## Parameters

 _ulCallerData_
  
> [in] Contains calling application information about the **IMessage** interface. 
    
 _lpMessage_
  
> [in] Pointer to the top-level message and attachments that have been released.
    
## Return value

None.
  

