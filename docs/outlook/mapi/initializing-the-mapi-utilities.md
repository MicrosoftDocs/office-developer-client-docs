---
title: "Initializing the MAPI Utilities"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 02b14285-bbef-44f2-b2a4-45d96395998a
 
 
---

# Initializing the MAPI Utilities

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
If the only part of MAPI that you need to use are the utilities — the interfaces and functions declared in MAPI's MAPIUTIL.H header file such as **IPropData** and **ITableData** — you do not need to call **MAPIInitialize** for initialization. For more information, see [IPropData : IMAPIProp](ipropdataimapiprop.md), [ITableData : IUnknown](itabledataiunknown.md), and [MAPIInitialize](mapiinitialize.md). Instead, call the **ScInitMapiUtil** function. For more information, see [ScInitMapiUtil](scinitmapiutil.md). **ScInitMapiUtil** enables client applications to use utility functions and methods that require MAPI allocators, but that do not ask for them explicitly. 
  
At shutdown time, make a call to **DeinitMapiUtil** to free resources connected to the utilities. Do not call **MAPIUninitialize**. For more information, see [DeinitMapiUtil](deinitmapiutil.md) and [MAPIUninitialize](mapiuninitialize.md).
  
Be aware that the **ITableData** interface does not support table notifications for clients that have called **ScInitMapiUtil** rather than **MAPIInitialize**. 
  

