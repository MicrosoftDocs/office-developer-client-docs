---
title: "OpenIMsgOnIStg"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- OpenIMsgOnIStg
api_type:
- HeaderDef
ms.assetid: a98b0b26-9b19-44ca-9b4e-0ad4d1c54325
description: "Last modified: March 09, 2015"
---

# OpenIMsgOnIStg

**Applies to**: Outlook 2013 | Outlook 2016
  
Builds a new [IMessage](imessageimapiprop.md) object on top of an existing OLE **IStorage** object, to be used within a message session.
  
|||
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |

```cpp
SCODE OpenIMsgOnIStg(
  LPMSGSESS lpMsgSess,
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPALLOCATEMORE lpAllocateMore,
  LPFREEBUFFER lpFreeBuffer,
  LPMALLOC lpmalloc,
  LPVOID lpMapiSup,
  LPSTORAGE lpStg,
  MSGCALLRELEASE FAR * lpfMsgCallRelease,
  ULONG ulCallerData,
  ULONG ulFlags,
  LPMESSAGE FAR * lppMsg
);
```

## Parameters

_lpMsgSess_
  
> [in] Pointer to a message session object within which the new **IMessage**-on- **IStorage** object is to be created.

_lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory.

_lpAllocateMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function, to be used to allocate additional memory.

_lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory.

_lpMalloc_
  
> [in] Pointer to a memory allocator object exposing the OLE **IMalloc** interface. The **IMessage** interface needs to use this allocation method when working with interfaces such as **IStorage** and **IStream**.

_lpMapiSup_
  
> [in] Optional pointer to a MAPI support object that a service provider can use to call the methods of the [IMAPISupport : IUnknown](imapisupportiunknown.md) interface.

_lpStg_
  
> [in, out] Pointer to an OLE **IStorage** object that is open and has read-only or read/write permission. Because **IMessage** does not support write-only access, **OpenIMsgOnIStg** does not accept a storage object opened in write-only mode.

_lpfMsgCallRelease_
  
> [in] Optional pointer to a callback function based on the [MSGCALLRELEASE](msgcallrelease.md) prototype that MAPI is to call following the last release on the **IMessage**-on- **IStorage** object.

_ulCallerData_
  
> [in] Caller data saved by MAPI with the **IMessage**-on- **IStorage** object and passed to the **MSGCALLRELEASE** based callback function. The data provides context about the **IMessage** object being released and the **IStorage** object on top of which it was built.

_ulFlags_
  
> [in] Bitmask of flags used to control whether the OLE **IStorage::Commit** method is called when the client application or service provider calls the **IMessage::SaveChanges** method. The following flags can be set:

IMSG_NO_ISTG_COMMIT
  
> The OLE method **IStorage::Commit** is not to be called when the client or provider calls [SaveChanges](imapiprop-savechanges.md).

MAPI_UNICODE
  
> Enables creation of Unicode .msg files. The resulting [IMessage](imessageimapiprop.md) file shows STORE_UNICODE_OK in its [PR_STORE_SUPPORT_MASK](pidtagstoresupportmask-canonical-property.md) and supports Unicode properties.

  > [!NOTE]
  > The MAPI_UNICODE flag is only supported in this function on Outlook 2003 or higher.
  
_lppMsg_
  
> [out] Pointer to a pointer to the opened **IMessage** object.

## Return value

S_OK
  
> The call succeeded and has returned the expected value or values.

## Remarks

Property attributes can only be accessed on property objects, that is, objects implementing the [IMAPIProp : IUnknown](imapipropiunknown.md) interface. To make MAPI properties available on an OLE structured storage object, **OpenIMsgOnIStg** builds an [IMessage : IMAPIProp](imessageimapiprop.md) object on top of the OLE **IStorage** object. The property attributes on such objects can be set or altered with [SetAttribIMsgOnIStg](setattribimsgonistg.md) and retrieved with [GetAttribIMsgOnIStg](getattribimsgonistg.md).
  
## Notes to callers

A message session should be opened with [OpenIMsgSession](openimsgsession.md) before **OpenIMsgOnIStg** is called. Supplying a valid  _lpMsgSess_ parameter make sures that the new message is created within a message session so that it is closed when the session is closed. If  _lpMsgSess_ is NULL, the message is created independently of any message session. If the client application or service provider that created the message does not release it, as well as all its attachments and open tables, memory is leaked and may cause the application to terminate.
  
MAPI uses the functions pointed to by _lpAllocateBuffer_, _lpAllocateMore_, and  _lpFreeBuffer_ for most memory allocation and deallocation, in particular to allocate memory for use by client applications when calling object interfaces such as [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPITable::QueryRows](imapitable-queryrows.md). The _lpAllocateBuffer_, _lpAllocateMore_, and _lpFreeBuffer_ pointers are optional when the **OpenIMsgOnIStg** function is called with a valid _lpMapiSup_ parameter.
  
Because it is dealing with an underlying OLE object, MAPI also needs to use OLE memory allocation. For more information about OLE structured storage objects and OLE memory allocation, see the  _OLE Programmer's Reference_.
  
If a valid value is supplied for _lpMapiSup_, **IMessage** supports the MAPI_DIALOG and ATTACH_DIALOG flags by calling the [IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md) method to supply a progress user interface for the [IMAPIProp::CopyTo](imapiprop-copyto.md) and [IMessage::DeleteAttach](imessage-deleteattach.md) methods. Also, the [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method attempts to convert short-term entry identifiers to long-term entry identifiers by calling the [IMAPISupport::OpenAddressBook](imapisupport-openaddressbook.md) method and making calls on the resulting address book object. If NULL is passed for _lpMapiSup_, **IMessage** ignores MAPI_DIALOG and ATTACH_DIALOG and stores short-term entry identifiers without conversion.
  
The **IStorage** object pointed to by the  _lpStg_ parameter must be opened in either the STGM_READ or STGM_READWRITE mode. If the STGM_READWRITE mode is used, the STGM_TRANSACTED mode must also be set.
  
The callback function pointed to by the _lpfMsgCallRelease_ parameter is optional; if provided, it should be based on the [MSGCALLRELEASE](msgcallrelease.md) function prototype. The **IMessage** interface calls it when the reference count of the **IMessage**-on- **IStorage** object is set to zero by the last call to its **Release** method. The callback function is commonly used to free the underlying **IStorage** interface. **IMessage** will not attempt to access the **IStorage** object pointed to by the _lpStg_ parameter after making the callback.
  
Some clients or providers might write additional data to the **IStorage** object beyond what **IMessage** itself writes when its [SaveChanges](imapiprop-savechanges.md) method is called. The client or provider can use the IMSG_NO_ISTG_COMMIT flag to prevent **IMessage** from calling the OLE **IStorage::Commit** method while processing a **SaveChanges** call; in this case the client or provider must itself commit the **IStorage** object when the additional data is written. To aid in this, the **IMessage** implementation guarantees to name all substorages it creates in the **IStorage** object starting with the string "__", that is, with two underscores. The client or provider can avoid name collisions by keeping its substorage names out of this namespace.
  
MAPI does not define the behavior of multiple open operations performed on a subobject of a message, such as an attachment, a stream, or an embedded message. MAPI currently allows a subobject that is already open to be opened once more, but MAPI performs the open operation by incrementing the reference count for the existing open object and returning it to the client or provider that called the [IMessage::OpenAttach](imessage-openattach.md) or [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method. This means the access requested for the first open operation on a subobject is the access provided for all subsequent open operations, regardless of the access requested by the operations.
  
The correct procedure for placing a message into an attachment is to call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method with an interface identifier of IID_IMessage. **OpenProperty** currently also supports creation of message attachments available directly on the OLE **IStorage** interface, that is, using the IID_IStorage interface identifier. **IStorage** access is supported to allow an easy way to put a Microsoft Word document into an attachment without converting it to or from the OLE **IStream** interface. However, **IMessage** may not behave predictably if **OpenIMsgOnIStg** is passed an **IStorage** pointer to the attachment data and then the objects are released in the wrong order.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|File.cpp  <br/> |LoadMSGToMessage  <br/> |MFCMAPI uses the **OpenIMsgOnIStg** method to open an IMessage interface on top of the .MSG file so that the file may be manipulated with MAPI. |

## See also

- [MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
