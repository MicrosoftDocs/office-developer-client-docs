---
title: "Invalidating an Object"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 7d601cee-ffc4-4c7c-8006-40b717dee247
 
 
---

# Invalidating an Object

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
As part of your provider's shutdown process, you might want to invalidate an object. Invalidating an object involves replacing its vtable with a vtable that contains implementations for the three **IUnknown** methods: **AddRef**, **Release**, and **QueryInterface**. Invalidate an object by calling [IMAPISupport::MakeInvalid](imapisupport-makeinvalid.md), a method that is included in the support object of each of the three common provider types. Providers typically make this call in the implementation of their logon object's **Logoff** method. 
  
Invalidating an object gives MAPI the ultimate responsibility for freeing the memory associated with an object. You can free all of the resources connected with an object and then call **MakeInvalid** to invalidate all of the methods in its inherited interfaces. Calls to any of these methods will return MAPI_E_INVALID_OBJECT. Using **MakeInvalid** is an option that many service providers choose to ignore. 
  
## See also



[Shutting Down a Service Provider](shutting-down-a-service-provider.md)

