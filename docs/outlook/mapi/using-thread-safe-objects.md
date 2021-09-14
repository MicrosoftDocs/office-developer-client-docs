---
title: "Using Thread-Safe Objects"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: e688db5e-d1a1-4afc-998f-b3d31eb6239b
description: "Last modified: July 23, 2011"
 
 
---

# Using Thread-Safe Objects

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Client applications can assume that objects used directly or as callbacks are always thread-safe except in the following cases:
  
- A transport provider's status object obtained through a client call to [IMAPISession::OpenEntry](imapisession-openentry.md) with an entry identifier from the provider's status table row. 
    
- All MAPI form objects obtained through a client call to [MAPIOpenFormMgr](mapiopenformmgr.md). Form objects obey apartment model rules and clients must use them and all objects contained by them only on the thread that created them.
    
When a client accesses a transport provider's row in the status table that includes the entry identifier of the associated status object, the client can call **OpenEntry** with that entry identifier to open the status object. This status object is not thread-safe because transport providers run in the context of the MAPI spooler and do not maintain a separate context for their status object. The status object obeys apartment model rules and clients must use it only on the thread that created it. 
  
A client must also invoke [MAPIInitialize](mapiinitialize.md) on every thread before using any MAPI objects and [MAPIUninitialize](mapiuninitialize.md) when that use is complete. These calls should be made even if the objects to be used are passed to the thread from an external source. **MAPIInitialize** and **MAPIUninitialize** can be called from anywhere except from within a Win32 **DllMain** function, a function that is invoked by the system when processes and threads are initialized and terminated, or upon calls to the **LoadLibrary** and **FreeLibrary** functions. 
  
Indirect use objects should never be assumed to be thread-safe. Indirect use objects are returned by methods that require destination interface pointers as input parameters. Examples of such methods are **IMAPIProp::CopyTo** and **CopyProps**, **IMAPIFolder::CopyFolder** and **CopyMessage**, and **IMsgServiceAdmin::CopyMsgService**. If a service provider wants to call such an object from a thread other than the one on which it was passed, the provider is responsible for explicitly marshaling the object.
  

