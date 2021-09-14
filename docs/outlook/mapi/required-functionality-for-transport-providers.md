---
title: "Required Functionality for Transport Providers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a0d9a3e0-a500-4d72-8859-ecfd1604fc5b
description: "Last modified: July 23, 2011"
 
 
---

# Required Functionality for Transport Providers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Every MAPI transport provider must:
  
- Follow the general guidelines for working with MAPI and other service providers. For more information, see [MAPI Application Development](mapi-application-development.md) and [MAPI Service Providers](mapi-service-providers.md).
    
- Have its transport provider DLL expose to MAPI its [XPProviderInit](xpproviderinit.md) initialization function. 
    
- Expose to MAPI its implementation of the [IXPProvider : IUnknown](ixpprovideriunknown.md) and [IXPLogon : IUnknown](ixplogoniunknown.md) interfaces. 
    
- Expose to MAPI and client applications its implementation of the [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) interface. For more information about implementing **IMAPIStatus**, see [Status Object Implementation](status-object-implementation.md). 
    
- Implement a property sheet dialog box for configuration. For more information about implementing property sheets, see [Property Sheet Implementation](property-sheet-implementation.md).
    

