---
title: "IMAPISupportNewUID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.NewUID
api_type:
- COM
ms.assetid: 7994477d-5207-4335-b538-69c98782d52d
description: "Last modified: July 23, 2011"
---

# IMAPISupport::NewUID

  
  
**Applies to**: Outlook 
  
Creates a new [MAPIUID](mapiuid.md) structure to be used as a unique identifier. 
  
```
HRESULT NewUID(
LPMAPIUID lpMuid
);
```

## Parameters

 _lpMuid_
  
> A pointer to the new **MAPIUID** structure. 
    
## Return value

S_OK 
  
> The new **MAPIUID** structure was created. 
    
## Remarks

The **IMAPISupport::NewUID** method is implemented for all support objects. Service providers and message services call **NewUID** whenever they need to generate a long-term unique identifier. A message store provider, for example, might call **NewUID** to obtain a **MAPIUID** to put in the **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) property of a newly created message.
  
## Notes to Callers

Do not confuse the **MAPIUID** structure that you register at logon time with the **MAPIUID** structures that the **NewUID** method creates. The **MAPIUID** structure that you register when you call the [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) method represents your address book or message store provider to MAPI and is used to distinguish entry identifiers that different providers create. This **MAPIUID** structure should be hard-coded and not obtained through a call to **NewUID**.
  
## See also

#### Reference

[MAPIUID](mapiuid.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

