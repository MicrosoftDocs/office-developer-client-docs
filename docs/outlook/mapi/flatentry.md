---
title: "FLATENTRY"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FLATENTRY
api_type:
- COM
ms.assetid: 03e53e08-9113-4101-84c9-ccf6d43127f6
description: "Last modified: March 09, 2015"
---

# FLATENTRY

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
An [ENTRYID](entryid.md) structure plus a byte count that specifies the size of the **ENTRYID** structure. 
  
|Property|Description|
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[cbFLATENTRY](cbflatentry.md), [CbNewFLATENTRY](cbnewflatentry.md) <br/> |
   
```cpp
typedef struct
{
  ULONG cb;
  BYTE abEntry[MAPI_DIM];
} FLATENTRY, FAR *LPFLATENTRY;

```

## Members

 **cb**
  
> Count of bytes in the **abEntry** member. 
    
 **abEntry**
  
> The complete entry identifier that includes the array of flags and binary data.
    
## Remarks

A **FLATENTRY** structure resembles an [ENTRYID](entryid.md) structure. However, there are some differences: 
  
- A **FLATENTRY** structure stores the size of the entry identifier; **ENTRYID** does not. 
    
- A **FLATENTRY** structure stores the flag data together with the rest of the entry identifier; **ENTRYID** stores them separately. 
    
- A **FLATENTRY** structure is used to store an entry identifier in a file or pass it in a stream of bytes whereas an **ENTRYID** structure is used by the [IMAPIProp](imapipropiunknown.md) interface methods and by the following **OpenEntry** methods: [IABLogon::OpenEntry](iablogon-openentry.md), [IAddrBook::OpenEntry](iaddrbook-openentry.md), [IMAPIContainer::OpenEntry](imapicontainer-openentry.md), [IMAPISession::OpenEntry](imapisession-openentry.md), [IMAPISupport::OpenEntry](imapisupport-openentry.md), [IMsgStore::OpenEntry](imsgstore-openentry.md), [IMSLogon::OpenEntry](imslogon-openentry.md)
    
- A **FLATENTRY** structure is used to store an entry identifier in a file or pass it in a stream of bytes. An **ENTRYID** structure is used to store an entry identifier on disk. 
    
## See also



[ENTRYID](entryid.md)


[MAPI Structures](mapi-structures.md)

