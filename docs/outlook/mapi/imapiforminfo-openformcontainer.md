---
title: "IMAPIFormInfoOpenFormContainer"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormInfo.OpenFormContainer
api_type:
- COM
ms.assetid: 1d6eec99-59f9-4700-9b83-7f7f8787a9f8
---

# IMAPIFormInfo::OpenFormContainer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
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



[IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md)

