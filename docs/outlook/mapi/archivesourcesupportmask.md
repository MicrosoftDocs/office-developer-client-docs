---
title: "ArchiveSourceSupportMask" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ArchiveSourceSupportMask
api_type:
- COM
ms.assetid: e35216e0-c23f-70f2-0d5f-1ac5dc00fd8c
description: "Specifies whether Microsoft Office Outlook should scan folders in a store and archive them automatically."
---

# ArchiveSourceSupportMask

**Applies to**: Outlook 2013 | Outlook 2016
  
Specifies whether Microsoft Office Outlook should scan folders in a store and archive them automatically.
  
## Quick info

|**Value**|**Description**|
|:-----|:-----|
|Exposed on:  <br/> |[IMsgStore : IMAPIProp](imsgstoreimapiprop.md) object  <br/> |
|Created by:  <br/> |Store provider  <br/> |
|Accessed by:  <br/> |Outlook and other clients  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Access type:  <br/> |Read-only or read/write depending on the store provider  <br/> |

## Remarks

To provide any of the store functionality, the store provider must implement [IMAPIProp : IUnknown](imapipropiunknown.md) and return a valid property tag for any of these properties passed to an [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) call. When the property tag for any of these properties is passed to [IMAPIProp::GetProps](imapiprop-getprops.md), the store provider must also return the correct property value. Store providers can call [HrGetOneProp](hrgetoneprop.md) and [HrSetOneProp](hrsetoneprop.md) to get or set these properties.
  
To retrieve the value of this property, the client should first use [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) to obtain the property tag, and then specify this property tag in [IMAPIProp::GetProps](imapiprop-getprops.md) to get the value. When calling [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md), specify the following values for the [MAPINAMEID](mapinameid.md) structure pointed at by the input parameter _lppPropNames_:
  
|**Value**|**Description**|
|:-----|:-----|
|lpGuid:  <br/> |PSETID_Common  <br/> |
|ulKind:  <br/> |MNID_STRING  <br/> |
|Kind.lpwstrName:  <br/> |L"ArchiveSourceSupportMask"  <br/> |

This property allows store providers to specify whether Outlook should scan folders in a store and archive them automatically.
  
By default, this property is not exposed on a store, which means Outlook can scan folders on the store. If the property is exposed, the following are the possible values:
  
```cpp
enum { 
 ASM_DEFAULT              = 0, 
 ASM_DO_NOT_ARCHIVE         = 1 << 0x0, 
 ASM_CLIENT_DO_NOT_CHANGE = 1 << 0xF 
};
```

ASM_DEFAULT
  
- Outlook can scan folders on the store.

ASM_DO_NOT_ARCHIVE
  
- Outlook should not scan folders on the store.

ASM_CLIENT_DO_NOT_CHANGE
  
- Do not allow clients to change this property on the store. Note that the constant **ASM_CLIENT_DO_NOT_CHANGE** is for future reference and is not currently implemented. For now, a store can prevent clients from changing this flag by hardcoding the value that the store returns for this property.
