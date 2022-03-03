---
title: "Supporting Named Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 2e742ecd-2dcd-46a8-9d4e-2cec2c6f795e
 
 
---

# Supporting Named Properties

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Any object that implements the [IMAPIProp : IUnknown](imapipropiunknown.md) interface can support named properties. Support for named properties is required for: 
  
- Address book providers that allow entries from other providers to be copied into their containers.
    
- Message store providers that can be used to create arbitrary message types.
    
Named property support is optional for all other service providers. Service providers that do support named properties must implement name-to-identifier mapping in the [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) and [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) methods. Clients call **GetNamesFromIDs** to retrieve the corresponding names for one or more property identifiers in the over 0x8000 range and **GetIDsFromNames** to either create or retrieve the identifiers for one or more names. 
  
Service providers that do not support named properties must:
  
- Fail calls to [IMAPIProp::SetProps](imapiprop-setprops.md) to set properties with identifiers of 0x8000 or greater by returning MAPI_E_UNEXPECTED_ID in the [SPropProblem](spropproblem.md) array. 
    
- Return MAPI_E_NO_SUPPORT from the [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) and [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) methods . 
    

