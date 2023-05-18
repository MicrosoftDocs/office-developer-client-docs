---
title: "IXPLogonAddressTypes"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IXPLogon.AddressTypes
api_type:
- COM
ms.assetid: 5add1f2b-d9e6-4d78-8739-c3848f6e32a3
---

# IXPLogon::AddressTypes

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the types of recipients that the transport provider handles.
  
```cpp
HRESULT AddressTypes(
  ULONG FAR * lpulFlags,
  ULONG FAR * lpcAdrType,
  LPSTR FAR * FAR * lpppszAdrTypeArray,
  ULONG FAR * lpcMAPIUID,
  LPUID FAR * FAR * lpppUIDArray
);
```

## Parameters

 _lpulFlags_
  
> [out] A bitmask of flags that controls the type of strings returned. The following flag can be set:
    
MAPI_UNICODE 
  
> The returned strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _lpcAdrType_
  
> [out] A pointer to the count of entries in the array pointed to by the  _lpppszAdrTypeArray_ parameter. 
    
 _lpppszAdrTypeArray_
  
> [out] A pointer to a pointer to an array of strings that identify recipient types.
    
 _lpcMAPIUID_
  
> [out] A pointer to the count of entries in the array pointed to by the  _lpppUIDArray_ parameter. 
    
 _lpppUIDArray_
  
> [out] A pointer to a pointer to an array of pointers to [MAPIUID](mapiuid.md) structures that identify recipient types. 
    
## Return value

S_OK 
  
> The transport provider successfully indicated the types of recipients that it can handle.
    
## Notes to implementers

The MAPI spooler calls the **IXPLogon::AddressTypes** method immediately after a transport provider returns from a call to the [IXPProvider::TransportLogon](ixpprovider-transportlogon.md) method so the transport provider can indicate what types of recipients it handles. To indicate this, the transport provider should pass back in the _lpppszAdrTypeArray_ parameter a pointer to an array of pointers to strings, or pass back in the _lpppUIDArray_ parameter a pointer to an array of pointers to **MAPIUID** structures, or pass values in both parameters. 
  
These two arrays are used for different identification processes. MAPI and the MAPI spooler use the [MAPIUID](mapiuid.md) structures in the _lpppUIDArray_ array to identify those recipient entry identifiers that are directly handled by the transport provider or by the messaging system to which the transport provider connects. Neither MAPI nor the MAPI spooler expands addresses by using entry identifiers contained in any of these **MAPIUID** structures; these structures are used only for recipient type identification. 
  
The MAPI spooler uses each of the strings in the _lpppszAdrTypeArray_ parameter for a comparison test when it decides which transport provider should handle which recipients for an outbound message. If a message recipient's **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md)) property exactly matches a string that identifies one of the messaging address types that the transport provider supplies, the provider can deliver the message to that recipient.
  
If multiple transport providers can handle the same type of recipient, MAPI selects a transport provider based on the transport priority order indicated in the client application's profile. To determine which transport provider to use, the MAPI spooler scans all provider-specified **MAPIUID** structures in priority order, and then all provider-specified address type values in priority order. The first transport provider to match a particular recipient in this scan gets the first opportunity to handle this recipient. If that provider does not handle the recipient, the MAPI spooler continues the scan to find a transport provider for any recipient not yet handled. The scan continues until no further matches are found, at which point a nondelivery report is generated for any recipient that was not handled. 
  
If the provider always supports a particular set of recipient types, the address type and **MAPIUID** arrays that the transport provider passed can be static. If the transport provider dynamically constructs these arrays, it can allocate memory by using the support object that was previously passed in the call to **TransportLogon**, although this is not necessary.
  
The memory used for the address type and **MAPIUID** arrays should remain allocated until the final call to the [IXPLogon::TransportLogoff](ixplogon-transportlogoff.md) method, at which time the transport provider can free the memory, if necessary. The transport provider should not alter the contents of these arrays after it returns from the **TransportLogoff** call. 
  
A transport provider that can handle any type of recipient can return NULL in the _lpppszAdrTypeArray_ parameter. Transport providers for LAN-based messaging systems that use a central server to deliver outgoing messages to various foreign message systems commonly do this. This type of transport provider should be installed last in the MAPI and MAPI spooler priority order of transport providers in the profile. 
  
A transport provider that does not support outbound messages that are dispatched to it based on address type should return a single zero-length string in  _lpppszAdrTypeArray_. If a transport provider supports no recipient types, it should pass NULL for the **MAPIUID** structure and an empty string for the address type. Transport providers of this type are most commonly used to install a message preprocessor. 
  
## See also



[IXPLogon::TransportLogoff](ixplogon-transportlogoff.md)
  
[IXPProvider::TransportLogon](ixpprovider-transportlogon.md)
  
[MAPIUID](mapiuid.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

