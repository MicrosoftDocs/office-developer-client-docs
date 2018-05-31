---
title: "IFolderSupportGetSupportMask"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IFolderSupport.GetSupportMask
api_type:
- COM
ms.assetid: 8d8aaeb7-57d7-ba4c-95d1-a5368cfc4afe
description: "Last modified: July 23, 2011"
---

# IFolderSupport::GetSupportMask

  
  
**Applies to**: Outlook 
  
Gets information about a folder's support for sharing.
  
```cpp
HRESULT GetSupportMask( 
    DWORD * pdwSupportMask 
); 
```

## Parameters

 _pdwSupportMask_
  
> [out] A bitmask indicating if the folder supports sharing.
    
 **FS_NONE**
  
> Indicates that the folder does not support sharing.
    
 **FS_SUPPORTS_SHARING**
  
> Indicates that the folder supports sharing.
    
## Return value

S_OK 
  
> The call was successful.
    

