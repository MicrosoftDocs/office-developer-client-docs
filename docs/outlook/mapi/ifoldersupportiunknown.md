---
title: "IFolderSupport  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IFolderSupport
api_type:
- COM
ms.assetid: a4b03a66-cf6d-cd20-f1df-b247d3ee87aa
description: "Last modified: March 09, 2015"
---

# IFolderSupport : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides information about a folder's support for sharing.
  
|||
|:-----|:-----|
|Provided by:  <br/> |Message store provider  <br/> |
|Interface identifier:  <br/> |IID_IFolderSupport  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|**[GetSupportMask](ifoldersupport-getsupportmask.md)** <br/> |Gets information about a folder's support for sharing.  <br/> |
   
## Remarks

Generally, Microsoft Office Outlook requires a MAPI store provider to implement this interface if the provider wants to share a folder. The exception is the Exchange Server store provider, which can share folders without implementing this interface.
  
A client can query an **[IMAPIFolder](imapifolderimapicontainer.md)** for **IFolderSupport**. If that succeeds, call **IFolderSupport::GetSupportMask** and check for the **FS_SUPPORTS_SHARING** bit to be set. 
  

