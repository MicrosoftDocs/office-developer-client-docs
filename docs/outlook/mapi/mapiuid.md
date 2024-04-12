---
title: "MAPIUID"
description: "MAPIUID is a byte-order independent version of a GUID structure that is used to uniquely identify a service provider."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.MAPIUID
api_type:
- COM
ms.assetid: 63eac3ee-e59b-4a06-8bb9-f72764d84bda
---

# MAPIUID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A byte-order independent version of a [GUID](guid.md) structure that is used to uniquely identify a service provider. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macro:  <br/> |[IsEqualMAPIUID](isequalmapiuid.md) <br/> |
   
```cpp
typedef struct _MAPIUID
{
  BYTE ab[16];
} MAPIUID, FAR *LPMAPIUID;

```

## Members

 **ab**
  
> An array that contains a 16-byte identifier.
    
## Remarks

A **MAPIUID** structure is a **GUID** structure put into Intel® processor byte order. 
  
MAPI creates **MAPIUID** structures in a way that makes it very rare for two different items to have the same identifier. **MAPIUID** structures can be stored as binary properties or as files, without regard to the byte ordering of the computer storing or accessing the information. 
  
 **MAPIUID** structures are used: 
  
- To identify a profile section.
    
- In the entry identifiers of message store and address book objects to identify the responsible service provider.
    
- In the **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) property of messages.
    
To generate a **MAPIUID** identifier for a search key, service providers call [IMAPISupport::NewUID](imapisupport-newuid.md).
  
When a client transmits a message across a network, it should use a protocol or transmission format that does not change the byte order of **MAPIUID** data. 
  
For more information about how **MAPIUID** structures are used, see the following topics: 
  
[Registering Service Provider Unique Identifiers](registering-service-provider-unique-identifiers.md)
  
[Setting Transport Order](setting-transport-order.md)
  
## See also



[GUID](guid.md)
  
[IMAPISession::OpenProfileSection](imapisession-openprofilesection.md)
  
[IMAPISupport::NewUID](imapisupport-newuid.md)


[MAPI Structures](mapi-structures.md)

