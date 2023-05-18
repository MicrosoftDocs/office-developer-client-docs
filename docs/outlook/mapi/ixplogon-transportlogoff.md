---
title: "IXPLogonTransportLogoff"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IXPLogon.TransportLogoff
api_type:
- COM
ms.assetid: b2b368ce-4486-4f90-985f-59e50ca95229
---

# IXPLogon::TransportLogoff

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Initiates the logoff process. 
  
```cpp
HRESULT TransportLogoff(
  ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values. If anything other than S_OK is returned, the provider is logged off.
    
## Remarks

The MAPI spooler calls the **IXPLogon::TransportLogoff** method to terminate a transport provider session for a particular user. Before calling **TransportLogoff**, the MAPI spooler discards any data about supported messaging address types for this session passed in the [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method. 
  
## Notes to implementers

The transport provider should be prepared to accept a call to **TransportLogoff** at any time. If a message is in process, the provider should stop the sending process. 
  
The transport provider should release all resources allocated for its current session. If it has allocated any memory for this session with the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, it should free the memory by using the [MAPIFreeBuffer](mapifreebuffer.md) function. Any memory allocated by the transport provider to satisfy calls to the [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method can be safely released at this time. 
  
Usually, on completing a **TransportLogoff** call, a provider should first invalidate its logon object by calling the [IMAPISupport::MakeInvalid](imapisupport-makeinvalid.md) method and then release its support object. The provider's implementation of **TransportLogoff** should release the support object last, because when the support object is released, the MAPI spooler can also release the provider object itself. 
  
## See also



[IMAPISupport::MakeInvalid](imapisupport-makeinvalid.md)
  
[IMAPISupport::SpoolerYield](imapisupport-spooleryield.md)
  
[IXPLogon::AddressTypes](ixplogon-addresstypes.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

