---
title: "Using the MAPI Utilities"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 5f0e5c97-5089-47cb-b604-2292b2ff945c
description: "Last modified: July 23, 2011"
 
 
---

# Using the MAPI Utilities

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The MAPI utilities are made up of table data and property data objects and a variety of functions to support miscellaneous features. It is possible for a client to need only these utilities and not have to log on to the MAPI subsystem to establish a connection with service providers. If your client fits into this category, call the API function [ScInitMapiUtil](scinitmapiutil.md) rather than the [MAPIInitialize](mapiinitialize.md) function at initialization time. 
  
 **ScInitMapiUtil** enables clients to use utility functions that require MAPI allocators, but that do not ask for the allocators explicitly. When it is time to shut down, call [DeinitMapiUtil](deinitmapiutil.md) to free resources rather than [MAPIUninitialize](mapiuninitialize.md). Clients that never call **MAPIInitialize** should not call **MAPIUninitialize**.
  
If you have called **ScInitMapiUtil** rather than **MAPIInitialize** and are using tables through the **ITableData** methods rather than through the **IMAPITable** methods, be aware that table notifications will not work. Notifications require the use of the MAPI libraries and [IMAPITable : IUnknown](imapitableiunknown.md).
  

