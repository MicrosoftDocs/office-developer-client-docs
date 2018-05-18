---
title: "IMAPIFormInfoOpenFormContainer"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormInfo.OpenFormContainer
api_type:
- COM
ms.assetid: 1d6eec99-59f9-4700-9b83-7f7f8787a9f8
description: "Last modified: July 23, 2011"
---

# IMAPIFormInfo::OpenFormContainer

  
  
**Applies to**: Outlook 
  
Returns a pointer to the form container in which a particular form is installed.
  
```cpp
HRESULT OpenFormContainer(
  LPMAPIFORMCONTAINER FAR * ppformcontainer
);
```

## Parameters

 _ppformcontainer_
  
> [out] A pointer to a pointer to the returned form container object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## See also

#### Reference

[IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md)

