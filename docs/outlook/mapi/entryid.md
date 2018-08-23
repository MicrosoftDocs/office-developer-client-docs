---
title: "ENTRYID"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ENTRYID
api_type:
- COM
ms.assetid: 8ebb21ca-5ad1-4dcc-97b6-2390664b5d8d
description: "Last modified: March 09, 2015"
---

# ENTRYID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an entry identifier for a MAPI object. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[CbNewENTRYID](cbnewentryid.md), [SizedENTRYID](sizedentryid.md) <br/> |
   
```cpp
typedef struct
{
  BYTE abFlags[4];
  BYTE ab[MAPI_DIM];
} ENTRYID, FAR *LPENTRYID;

```

## Members

 **abFlags**
  
> Bitmask of flags that provide information that describes the object. Only the first byte of the flags, **abFlags[0]**, may be set by the provider; the other three are reserved. These flags must not be set for permanent entry identifiers; they are only set for short-term entry identifiers. To clients, this structure is read-only. The following flags can be set in **abFlags[0]**:
    
MAPI_NOTRECIP 
  
> The entry identifier cannot be used as a recipient on a message.
    
MAPI_NOTRESERVED 
  
> Other users cannot access the entry identifier.
    
MAPI_NOW 
  
> The entry identifier cannot be used at other times.
    
MAPI_SHORTTERM 
  
> The entry identifier is short-term. All other values in this byte must be set unless other uses of the entry identifier are enabled.
    
MAPI_THISSESSION 
  
> The entry identifier cannot be used on other sessions.
    
 **ab**
  
> Indicates an array of binary data that is used by service providers. The client application cannot use this array.
    
## Remarks

The **ENTRYID** structure is used by message store and address book providers to construct unique identifiers for their objects. Entry identifiers are used to identify the following types of objects: 
  
- Message stores
    
- Folders
    
- Messages
    
- Address book containers
    
- Distribution lists
    
- Messaging users
    
- Status objects
    
- Profile sections
    
Each provider uses a format for the **ENTRYID** structure that makes sense for that provider. 
  
Entry identifiers cannot be compared directly because one object can be represented by two different binary values. To determine whether two entry identifiers represent the same object, call the [IMAPISession::CompareEntryIDs](imapisession-compareentryids.md) method. 
  
When a client calls an object's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve its entry identifier, the object returns the most permanent form of the entry identifier. A client can verify that an entry identifier is long-term by checking that none of the flags are set in the first byte of the **abFlags** member. 
  
When a client accesses an entry identifier through a column in a table, most likely this entry identifier is short-term instead of long-term. Short-term entry identifiers can be used to open their corresponding objects only in the current MAPI session. A client can verify that an entry identifier is short-term by checking that all of the flags are set in the first byte of the **abFlags** member. 
  
Some entry identifiers are short-term, but have long-term use. Such an entry identifier will have one or more of the appropriate flags set in the first byte of its **abFlags** member. 
  
An **ENTRYID** structure resembles a [FLATENTRY](flatentry.md) structure. However, there are some differences: 
  
- An **ENTRYID** structure does not store the size of the entry identifier; a **FLATENTRY** structure does. 
    
- An **ENTRYID** structure stores the flag data and the rest of the entry identifier separately; a **FLATENTRY** structure stores the flag data with the rest of the entry identifier. 
    
- An **ENTRYID** structure is passed as a parameter to the methods of the [IMAPIProp](imapipropiunknown.md) interface and to the following **OpenEntry** methods: [IABLogon::OpenEntry](iablogon-openentry.md), [IAddrBook::OpenEntry](iaddrbook-openentry.md), [IMAPIContainer::OpenEntry](imapicontainer-openentry.md), [IMAPISession::OpenEntry](imapisession-openentry.md), [IMAPISupport::OpenEntry](imapisupport-openentry.md), [IMsgStore::OpenEntry](imsgstore-openentry.md), [IMSLogon::OpenEntry](imslogon-openentry.md)
    
- An **ENTRYID** structure is used to store an entry identifier on disk. A **FLATENTRY** structure is used to store an entry identifier in a file or pass it in a stream of bytes. 
    
Clients should always pass in naturally aligned entry identifiers. Although providers should handle arbitrarily aligned entry identifiers, clients should not expect this behavior. Failure to pass a good aligned entry identifier to a method can cause an alignment fault on RISC processors. 
  
The natural alignment factor, typically 8 bytes, is the largest data type supported by the CPU, and usually the same alignment factor used by the system memory allocator. A naturally aligned memory address allows the CPU to access any data type it supports at that address without generating an alignment fault. For RISC CPUs, a data type of size N bytes must usually be aligned on an even multiple of N bytes, with the address being an even multiple of N.
  
For more information, see [Entry Identifiers](mapi-entry-identifiers.md). 
  
## See also



[FLATENTRY](flatentry.md)
  
[IMAPISupport::CompareEntryIDs](imapisupport-compareentryids.md)
  
[PidTagRecordKey Canonical Property](pidtagrecordkey-canonical-property.md)


[MAPI Structures](mapi-structures.md)

