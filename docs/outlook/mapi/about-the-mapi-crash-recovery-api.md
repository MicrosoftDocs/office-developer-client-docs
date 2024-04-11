---
title: "About the MAPI Crash Recovery API"
description: "Describes the MAPI Crash Recovery API, which checks the state of the Personal Folders file (PST) or Offline Folders file (OST) shared memory to verify that the data is in a consistent state."
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: bc1e1f55-1959-a4a9-a24d-f006af531c9a
 
 
---

# About the MAPI Crash Recovery API

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The MAPI Crash Recovery API checks the state of the Personal Folders file (PST) or Offline Folders file (OST) shared memory to verify that the data is in a consistent state. If it is in a consistent state, the [MAPICrashRecovery](mapicrashrecovery.md) function moves the data from the open PSTs or OSTs to disk and locks the PSTs or OSTs and does not allow any read or write access to the data. This ensures that the data remains in a consistent state until the process is terminated. By ensuring that the PSTs or OSTs are in a consistent state before the process is terminated, you can prevent Microsoft Outlook 2013 and Microsoft Outlook 2010 from displaying the following error message and avoid performance problems. 
  
 **A data file did not close properly the last time it was used and is being checked for problems. Performance might be affected while the check is in progress.**
  
This API provides the following:
  
Constants:
  
- [MAPI Constants](mapi-constants.md)
    
Functions:
  
- [MAPICrashRecovery](mapicrashrecovery.md)
    
## See also



[Use the MAPI Crash Recovery API](how-to-use-the-mapi-crash-recovery-api.md)

