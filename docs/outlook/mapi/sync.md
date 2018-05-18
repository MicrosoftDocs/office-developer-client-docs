---
title: "SYNC"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f07fddf-4c42-6ea7-162d-57022166a83f
description: "Last modified: July 23, 2011"
---

# SYNC

  
  
**Applies to**: Outlook 
  
Information for starting synchronization between a local store and a server. This information is used during the [synchronize state](synchronize-state.md).
  
## Quick Info

```cpp
struct SYNC 
{ 
    ULONG ulFlags; 
    LPWSTR pwzPath; 
    FEID Reserved1; 
    MEID Reserved2; 
    LPENTRYLIST pel; 
    ULONG const * pulFolderOptions; 
};
```

## Members

 _ulFlags_
  
- [out]/[in] A bitmask of the following flags that modifies the behavior during synchronization:
    
- UPS_UPLOAD_ONLY
    
  - [in] The client will be performing only upload. Outlook only returns locally modified folders.
    
- UPS_DNLOAD_ONLY
    
  - [in] The client will be performing only download. Outlook should not clear upload bits for folders.
    
- UPS_THESE_FOLDERS
    
  - [in] The client will be synchronizing a specified set of folders with the provided entry IDs. This flag can be combined with either the **UPS_UPLOAD_ONLY** or **UPS_DNLOAD_ONLY** flag. 
    
- UPS_OK
    
  - [out] Synchronization was successful. The client sets this after uploading or a full synchronization completes.
    
- 
    
    > [!NOTE]
    > Even though the client can either upload or fully synchronize (upload then download) folders and items with the Replication API, the client specifies  *ulFlags*  with only one direction of the replication at a time — either the **UPS_UPLOAD_ONLY** or **UPS_DNLOAD_ONLY** flag. In the case of a full synchronization, the client first does an upload with the **UPS_UPLOAD_ONLY** flag, and then a download with the **UPS_DNLOAD_ONLY** flag. 
  
 _pwzPath_
  
- [out] Path to the local store.
    
 _Reserved1_
  
- This member is reserved for the internal use of Outlook and is not supported.
    
 _Reserved2_
  
- This member is reserved for the internal use of Outlook and is not supported.
    
 *pel* 
  
- [in] This is the list of entry IDs of the folders to synchronize if **UPS_THESE_FOLDERS** has been set. See mapidefs.h for the type definition of **LPENTRYLIST**. 
    
 _pulFolderOptions_
  
- [in] This is an array of folder options for corresponding folders in  *pel*  if **UPS_THESE_FOLDERS** has been set. These folder options are used when uploading each of the folders listed in  *pel*  during the [upload folder state](upload-folder-state.md). For more information about folder options, see **[UPFLD](upfld.md)**. 
    
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)

