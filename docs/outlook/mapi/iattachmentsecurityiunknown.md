---
title: "IAttachmentSecurity  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAttachmentSecurity
api_type:
- COM
ms.assetid: 69609f73-5884-9e2b-ab78-a2e0ece3a1d1
description: "Last modified: March 09, 2015"
---

# IAttachmentSecurity : IUnknown

  
  
**Applies to**: Outlook 
  
Allows Microsoft Outlook 2010 and Microsoft Outlook 2013 solutions to find out if an attachment is considered unsafe and blocked for viewing and indexing.
  
|||
|:-----|:-----|
|Interface identifier:  <br/> |IID_IAttachmentSecurity  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[IAttachmentSecurity::IsAttachmentBlocked](iattachmentsecurity-isattachmentblocked.md) <br/> |Checks if a specified attachment is blocked by Outlook 2010 or Outlook 2013 for viewing and indexing.  <br/> |
   
## Remarks

Outlook 2010 and Outlook 2013 solutions can query this interface to see if an attachment is blocked. The attachments that are blocked by Outlook 2010 or Outlook 2013 vary depending on how Outlook 2010 or Outlook 2013 has been configured and the policies that an administrator has applied.
  
## See also

#### Concepts

[MAPI Constants](mapi-constants.md)
  
[How to: Verify an Attachment is Blocked](how-to-verify-an-attachment-is-blocked.md)

