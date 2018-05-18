---
title: "MAPICrashRecovery"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPICrashRecovery
api_type:
- COM
ms.assetid: 4172e2d3-6343-385b-c691-a64c1e198051
description: "Last modified: March 09, 2015"
---

# MAPICrashRecovery

  
  
**Applies to**: Outlook 
  
The **MAPICrashRecovery** function checks the state of the Personal Folders file (PST) or Offline Folders file (OST) shared memory. If the memory is in a consistent state, the **MAPICrashRecovery** function moves the data to disk and prevents further read or write access until the process is terminated. 
  
## Quick Info

|||
|:-----|:-----|
|Exported by:  <br/> |olmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
   
```cpp
void MAPICrashRecovery(ULONG ulFlags);
```

## Parameters

 _ulFlags_
  
> [in] Flags used to control how the MAPI crash recovery is performed. The following flags can be set:
    
    - **MAPICRASH_RECOVER**
    
  - If the PSTs or OSTs are in a consistent state, move the data to disk and lock the PSTs or OSTs to prevent read or write access.
    
    - **MAPICRASH_CONTINUE**
    
  - Unlock the PSTs or OSTs for debugging. After a successful call to **MAPICrashRecovery** with the **MAPICRASH_RECOVER** flag, call **MAPICrashRecovery** with the **MAPICRASH_CONTINUE** flag to allow debugging to continue. 
    
    - **MAPICRASH_SYSTEM_SHUTDOWN**
    
  - If the PSTs or OSTs are in a consistent state, move the data to disk and lock the PSTs or OSTs to prevent read or write access. The PSTs or OSTs cannot be unlocked using **MAPICRASH_CONTINUE**. Must be used in combination with **MAPICRASH_RECOVER**. 
    
## Remarks

The upper byte (0xFF000000) is reserved for provider specific crash recovery flags.
  
Call **MAPICrashRecovery** with the **MAPICRASH_RECOVER** and **MAPICRASH_SYSTEM_SHUTDOWN** flags in response to the **WM_ENDSESSION** message. 
  
## See also

#### Concepts

[About the MAPI Crash Recovery API](about-the-mapi-crash-recovery-api.md)
  
[Use the MAPI Crash Recovery API](how-to-use-the-mapi-crash-recovery-api.md)

