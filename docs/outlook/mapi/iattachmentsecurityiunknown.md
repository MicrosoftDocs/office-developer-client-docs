---
title: "IAttachmentSecurity  IUnknown"
description: Allows Microsoft Outlook 2010 and Microsoft Outlook 2013 solutions to find out if an attachment is considered unsafe and blocked for viewing and indexing.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IAttachmentSecurity
api_type:
- COM
ms.assetid: 69609f73-5884-9e2b-ab78-a2e0ece3a1d1
---

# IAttachmentSecurity : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Allows Microsoft Outlook 2010 and Microsoft Outlook 2013 solutions to find out if an attachment is considered unsafe and blocked for viewing and indexing.
  
|Property |Value |
|:-----|:-----|
|Interface identifier:  <br/> |IID_IAttachmentSecurity  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[IAttachmentSecurity::IsAttachmentBlocked](iattachmentsecurity-isattachmentblocked.md) <br/> |Checks if a specified attachment is blocked by Outlook 2010 or Outlook 2013 for viewing and indexing. |
   
## Remarks

Outlook 2010 and Outlook 2013 solutions can query this interface to see if an attachment is blocked. The attachments that are blocked by Outlook 2010 or Outlook 2013 vary depending on how Outlook 2010 or Outlook 2013 has been configured and the policies that an administrator has applied.
  
## See also



[MAPI Constants](mapi-constants.md)
  
[Verify an Attachment is Blocked](how-to-verify-an-attachment-is-blocked.md)

