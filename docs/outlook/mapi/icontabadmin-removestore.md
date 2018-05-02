---
title: "IContabAdminRemoveStore"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IContabAdmin.RemoveStore
api_type:
- COM
ms.assetid: 2a5fcf5c-8a5a-4774-b8c9-1ac1ff27947d
description: "Last modified: July 23, 2011"
---

# IContabAdmin::RemoveStore

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Removes the Contact Address Book (CAB) specified by the given entry ID from the address book hierarchy.
  
```VB.net
HRESULT RemoveStore(
ULONG cbEntryID, 
LPENTRYID lpEntryID
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the object to open.
    

