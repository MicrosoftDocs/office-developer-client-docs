---
title: "IOlkAccountHelperGetIdentity"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: ea8b8f02-959f-cd71-9cfe-5ebdf4bae2bc
description: "Gets the profile name of an account."
---

# IOlkAccountHelper::GetIdentity

Gets the profile name of an account.
  
## Quick info

See [IOlkAccountHelper](iolkaccounthelper.md).
  
```
HRESULT IOlkAccountHelper::GetIdentity (  
    LPWSTR pwszIdentity, 
    DWORD *pcch 
);
```

## Parameters

 _pwszIdentity_
  
> [in][out] The profile name.
    
 _pcch_
  
> [in] [out] Upon calling this method, contains the size (in number of characters) of  _pwszIdentity_ that has been allocated. Upon return, contains the actual length, including the 0-terminating character, of the returned profile name. 
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_OUTOFMEMORY  <br/> |The returned profile name is longer than the size of  _pwszIdentity_.  <br/> |
|E_INVALIDARG  <br/> | _pcch_ is NULL.  <br/> |
   
## Remarks

If  _pwszIdentity_ is too small to hold the profile name, it will not be set on return, and  _pcch_ will point to the size required for  _pwszIdentity_.
  
## See also



[About the Account Management API](about-the-account-management-api.md)


[PidTagProfileName](http://msdn.microsoft.com/library/13ca726d-ae7a-4da9-9c8e-3db3c479f839%28Office.15%29.aspx)

