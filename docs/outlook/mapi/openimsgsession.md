---
title: "OpenIMsgSession"
description: "Describes the syntax, parameters, and return value of OpenIMsgSession, which creates and opens a message session that groups the messages created within it."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.OpenIMsgSession
api_type:
- COM
ms.assetid: f75229e3-5f44-4298-8706-9eddf0ef124c
---

# OpenIMsgSession

**Applies to**: Outlook 2013 | Outlook 2016
  
Creates and opens a message session that groups the messages created within it.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |

```cpp
SCODE OpenIMsgSession(
  LPMALLOC lpMalloc,
  ULONG ulFlags,
  LPMSGSESS FAR * lppMsgSess
);
```

## Parameters

 _lpMalloc_

> [in] Pointer to a memory allocator object exposing the OLE [IMalloc](https://docs.microsoft.com/windows/desktop/api/objidl/nn-objidl-imalloc) interface. MAPI needs to use this allocation method when working with the OLE [IStorage](https://docs.microsoft.com/windows/desktop/api/objidl/nn-objidl-istorage) interface.

 _ulFlags_

> [in] Reserved; must be zero.

 _lppMsgSess_

> [out] Pointer to a pointer to the returned message session object.

## Return value

S_OK

> The session was opened.

MAPI_E_INVALID_PARAMETER

> _lpMalloc_ or _lppMsgSess_ is NULL.

MAPI_E_INVALID_FLAGS

> Invalid flags were passed.

MAPI_UNICODE

> When calling this function, a client or service provider sets the MAPI_UNICODE flag to create Unicode .msg files. The resulting [Imessage](imessageimapiprop.md) file shows STORE_UNICODE_OK in its PR_STORE_SUPPORT_MASK and supports Unicode properties.

## Remarks

A message session is used by client applications and service providers that want to deal with several related MAPI [IMessage : IMAPIProp](imessageimapiprop.md) objects built on top of underlying OLE **IStorage** objects. The client or provider uses the **OpenIMsgSession** and [CloseIMsgSession](closeimsgsession.md) functions to wrap the creation of such messages inside a message session. Once the message session is opened, the client or provider passes a pointer to it in a call to [OpenIMsgOnIStg](openimsgonistg.md) to create a new **IMessage**-on- **IStorage** object.

A message session keeps track of all **IMessage**-on- **IStorage** objects created during the duration of the session, in addition to all the attachments and other properties of the messages. When a client or provider calls **CloseIMsgSession**, it closes all these objects. Calling **CloseIMsgSession** is the only way to close **IMessage**-on- **IStorage** objects.

 **OpenIMsgSession** is used by clients and providers that require the ability to handle several related messages as OLE **IStorage** objects. If only one such message is to be open at a time, there is no need to track multiple messages and no reason to create a message session with **OpenIMsgSession**.

Because it is dealing with an underlying OLE object, MAPI needs to use OLE memory allocation. For more information about OLE structured storage objects and OLE memory allocation, see [OLE and Data Transfer](https://msdn.microsoft.com/library/d4a57956-37ba-44ca-8efc-bf617ad5e77b.aspx).
 