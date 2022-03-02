---
title: "PreprocessMessage"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PreprocessMessage
api_type:
- COM
ms.assetid: dda50325-74b3-445e-986e-115f6536561f
description: "Last modified: March 09, 2015"
---

# PreprocessMessage

**Applies to**: Outlook 2013 | Outlook 2016
  
Defines a function that preprocesses message contents or the format of a message.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Defined function implemented by:  <br/> |Transport providers  <br/> |
|Defined function called by:  <br/> |MAPI spooler  <br/> |

```cpp
HRESULT PreprocessMessage(
  LPVOID lpvSession,
  LPMESSAGE lpMessage,
  LPADRBOOK lpAdrBook,
  LPMAPIFOLDER lpFolder,
  LPALLOCATEBUFFER AllocateBuffer,
  LPALLOCATEMORE AllocateMore,
  LPFREEBUFFER FreeBuffer,
  ULONG FAR * lpcOutbound,
  LPMESSAGE FAR * FAR * lpppMessage,
  LPADRLIST FAR * lppRecipList
);
```

## Parameters

 _lpvSession_
  
> [in] Pointer to the session to be used.

 _lpMessage_
  
> [in] Pointer to the message to be preprocessed.

 _lpAdrBook_
  
> [in] Pointer to the address book from which the user should select recipients for the message.

 _lpFolder_
  
> [in, out] Pointer to a folder. On input, the _lpFolder_ parameter points to the folder that contains messages to be preprocessed. On output, _lpFolder_ points to the folder where preprocessed messages have been placed.

 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory.

 _lpAllocateMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function, to be used to allocate additional memory where required.

 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory.

 _lpcOutbound_
  
> [out] Pointer to the number of messages in the array pointed to by the _lpppMessage_ parameter.

 _lpppMessage_
  
> [out] Pointer to a pointer to an array of pointers to preprocessed or otherwise generated messages.

 _lppRecipList_
  
> [out] Pointer to an optional returned [ADRLIST](adrlist.md) structure, listing preprocessor-detected recipients for which the message is undeliverable. For more information about the contents of this list, see the [IMAPISupport::StatusRecips](imapisupport-statusrecips.md) method.

## Return value

S_OK
  
> Message contents were successfully preprocessed.

## Remarks

A transport-provider message preprocessor can present a progress indicator during message preprocessing. However, it should never present a dialog box requiring user interaction during message preprocessing.
  
When a preprocessor adds large amounts of data to an outbound message, certain procedures should be followed. This type of message can be stored in a server-based message store, causing the preprocessor to access a remote store, a time-consuming procedure. To avoid having to do so, the preprocessor should have an option that enables it to store data that takes a large amount of space in a local message store and to provide a reference to that local store in the message.
  
The preprocessor should not release any of the objects originally passed to the **PreprocessMessage** based function.
  
Before the MAPI spooler can call a **PreprocessMessage** function, the transport provider must have registered the function in a call to the [IMAPISupport::RegisterPreprocessor](imapisupport-registerpreprocessor.md) method. After calling a **PreprocessMessage** function, the spooler cannot continue submitting a message until the function returns.
  
The MAPI spooler owns the task of submitting messages. This means the original message is never placed in an array of message pointers and that a call to the **SubmitMessage** methods is never required.
  
## See also

[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)  
[IMAPISupport : IUnknown](imapisupportiunknown.md)
