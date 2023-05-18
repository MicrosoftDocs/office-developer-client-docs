---
title: "HrGetAutoDiscoverXML" 
description: This article describes the HrGetAutoDiscoverXML function and provides syntax, parameters, and return value.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- HrGetAutoDiscoverXML
api_type:
- COM
ms.assetid: 03691187-7c65-620b-576f-6ebe62a80830
---

# HrGetAutoDiscoverXML

**Applies to**: Outlook 2013 | Outlook 2016

Returns an Extensible Markup Language (XML) stream that represents information retrieved from the auto-discovery service of a Microsoft Exchange 2007 server.

## Quick info

|Property |Value |
|:-----|:-----|
|Exported by:  <br/> |olmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |

```cpp
HRESULT HrGetAutoDiscoverXML( 
    __in_z const WCHAR *pwzAddress, 
    __in_opt_z const WCHAR *pwzPassword, 
    __in_opt HANDLE hCancelEvent, 
    __in_opt ULONG ulFlags, 
    __out IStream** ppXmlStream); 

```

## Parameters

 _pwzAddress_

> [in] A null-terminated Simple Mail Transfer Protocol (SMTP) email address of the account for which you want to retrieve the auto-discovery information.

 _pwzPassword_

> [in] An optional password for the account specified by _pwzAddress_. Note that passing any password has no effect if the account specified by  _pwzAddress_ does not require a password.

 _hCancelEvent_

> [in] An unset Win32 event handle that is optional and can be used to cancel the operation. To cancel the operation, set the event and pass the event handle as _hCancelEvent_; pass **null** if you do not want to cancel the operation. Note that passing a value that does not represent an event handle has no effect and is ignored by the function.

 _ulFlags_

> [in] This parameter is not used. It must be 0.

 _ppXmlStream_

> [out] A pointer to an [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) object that contains the autodiscovery XML. Returns **null** if the autodiscovery operation fails. You must release the [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) object when you are finished with it.

## Return values

S_OK

- The function call is successful.

E_INVALIDARG

- _pwzAddress_ is **null** or is not a valid SMTP address, or _ppXmlStream_ is a **null** pointer to an [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) object.

MAPI_E_NOT_FOUND

- Client computer is not connected to the network, client computer is not connected to a Microsoft Exchange 2007 server, _pwzAddress_ is not an account on an Exchange 2007 server, or _pwzAddress_ is an account that does not support Exchange auto-discovery service.

MAPI_E_USER_CANCEL

- An event handle has been passed to _hCancelEvent_ to cancel the operation.

STRSAFE_E_INSUFFICIENT_BUFFER

- The value passed to _pwzAddress_ or _pwzPassword_ is too long, such that it overflows the internal buffer of size 256 bytes.
