---
title: "IAttachmentSecurityIsAttachmentBlocked"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAttachmentSecurity.IsAttachmentBlocked
api_type:
- COM
ms.assetid: 6986d27a-9602-e44a-0797-4c47f2184ef7
description: "Last modified: June 25, 2012"
---

# IAttachmentSecurity::IsAttachmentBlocked

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Checks if a specified attachment is blocked by Microsoft Outlook 2010 or Microsoft Outlook 2013 for viewing and indexing.
  
```cpp
HRESULT IAttachmentSecurity::IsAttachmentBlocked( 
    LPCWSTR pwszFileName,  
    BOOL *pfBlocked 
);
```

## Parameters

 _pwszFileName_
  
> [in] Pointer to the filename of an attachment.
    
 _pfBlocked_
  
> [out] Pointer to a value indicating **true** if the specified attachment is blocked; otherwise, **false**.
    
## See also



[MAPI Constants](mapi-constants.md)
  
[Verify an Attachment is Blocked](how-to-verify-an-attachment-is-blocked.md)

