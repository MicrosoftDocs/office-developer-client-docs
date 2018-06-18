---
title: "UPFLD"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6da9d6b6-a016-ccef-77da-3e037c30450d
description: "Last modified: July 23, 2011"
---

# UPFLD

**Applies to**: Outlook 2013 | Outlook 2016 
  
Information for uploading a folder during the [upload folder state](upload-folder-state.md).
  
## Quick info

```cpp
struct UPFLD 
{ 
    ULONG ulFlags; 
    LPMAPIFOLDER pfld; 
    FEID feid; 
}; 

```

## Members

_ulFlags_
  
>  [out]/[in] Flags to determine appropriate actions for the uplaod. 
    
  - UPF_NEW
    
    - [out] Folder is new.
    
  - UPF_MOD_PARENT
    
    - [out] Folder has been moved.
    
  - UPF_MOD_PROPS
    
    - [out] Folder properties have been modified.
    
  - UPF_DEL
    
    - [out] Folder was deleted.
    
  - UPF_OK
    
    - [in] Upload was successful. The client sets this after uploading folder information to the server.
    
_pfld_
  
> [out] The open folder object to upload.
    
_feid_
  
> [out] Entry ID of the folder.
    
## See also

- [About the Replication API](about-the-replication-api.md) 
- [About the Replication State Machine](about-the-replication-state-machine.md)
- [MAPI Constants](mapi-constants.md)

