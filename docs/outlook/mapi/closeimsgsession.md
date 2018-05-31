---
title: "CloseIMsgSession"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.CloseIMsgSession
api_type:
- COM
ms.assetid: a0a17309-fc59-4822-be9b-b6f623b68bb1
description: "Last modified: March 09, 2015"
---

# CloseIMsgSession

  
  
**Applies to**: Outlook 
  
Closes a message session and all the messages created within that session. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
VOID CloseIMsgSession(
  LPMSGSESS lpMsgSess
);
```

## Parameters

 _lpMsgSess_
  
> [in] Pointer to the message session object obtained using the [OpenIMsgSession](openimsgsession.md) function at the start of the message session. 
    
## Return value

None.
  
## Remarks

A message session is used by client applications and service providers that want to deal with several related MAPI **IMessage** objects built on top of underlying OLE **IStorage** objects. The client or provider uses the [OpenIMsgSession](openimsgsession.md) and **CloseIMsgSession** functions to wrap the creation of such messages inside a message session. Once the message session is opened, the client or provider passes a pointer to it in a call to [OpenIMsgOnIStg](openimsgonistg.md) to create a new **IMessage**-on- **IStorage** object. 
  
A message session keeps track of all **IMessage**-on- **IStorage** objects opened during the duration of the session, in addition to all the attachments and other properties of the messages. When a client or provider calls **CloseIMsgSession**, it closes all these objects. Calling **CloseIMsgSession** is the only way to close **IMessage**-on- **IStorage** objects. 
  

