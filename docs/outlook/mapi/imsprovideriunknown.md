---
title: "IMSProvider  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMSProvider
api_type:
- COM
ms.assetid: 0f17aa44-abcb-4732-b013-d91652847cf6
description: "Last modified: March 09, 2015"
---

# IMSProvider : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to a message store provider through a message store provider object. This message store provider object is returned at provider logon by the message store provider's [MSProviderInit](msproviderinit.md) entry point function. The message store provider object is primarily used by client applications and the MAPI spooler to open message stores. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Message store provider objects  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |MAPI and the MAPI spooler  <br/> |
|Interface identifier:  <br/> |IID_IMSProvider  <br/> |
|Pointer type:  <br/> |LPMSPROVIDER  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[Shutdown](imsprovider-shutdown.md) <br/> |Closes a message store provider in an orderly fashion.  <br/> |
|[Logon](imsprovider-logon.md) <br/> |Logs MAPI on to one instance of a message store provider.  <br/> |
|[SpoolerLogon](imsprovider-spoolerlogon.md) <br/> |Logs the MAPI spooler on to a message store.  <br/> |
|[CompareStoreIDs](imsprovider-comparestoreids.md) <br/> |Compares two message store entry identifiers to determine whether they refer to the same store object.  <br/> |
   
## Remarks

MAPI uses one message store provider object per session, no matter how many message stores are opened by the store provider. If a second MAPI session logs on to any open stores, MAPI calls **MSProviderInit** a second time to create a new message store provider object for that session to use. 
  
A message store provider object must contain the following to operate correctly:
  
- An  _lpMalloc_ memory-allocation routine pointer for use by all stores opened by using this provider object. 
    
- The  _lpfAllocateBuffer_,  _ lpfAllocateMore _, and  _lpfFreeBuffer_ routine pointers to the [MAPIAllocateBuffer](mapiallocatebuffer.md), [MAPIAllocateMore](mapiallocatemore.md), and [MAPIFreeBuffer](mapifreebuffer.md) memory allocation functions. 
    
- A linked list of all the stores opened by using this provider object and not yet closed.
    
## See also



[MAPI Interfaces](mapi-interfaces.md)

