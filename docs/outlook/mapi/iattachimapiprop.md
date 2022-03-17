---
title: "IAttach  IMAPIProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAttach
api_type:
- COM
ms.assetid: f47e20e1-2a30-4c9e-8ca6-e8c5e72f44a1
description: "Last modified: March 09, 2015"
---

# IAttach : IMAPIProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Maintains and provides access to the properties of attachments in messages. The **IAttach** interface has no unique methods of its own. For more information about how to use attachments, see [MAPI Attachments](mapi-attachments.md) and [Attachment Tables](attachment-tables.md). 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Attachment objects  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IAttachment  <br/> |
|Pointer type:  <br/> |LPATTACH  <br/> |
|Transaction model:  <br/> |Transacted  <br/> |
   
## Vtable order

This interface does not have any unique methods.
  
|**Required properties**|**Access**|
|:-----|:-----|
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_ATTACH_METHOD** ([PidTagAttachMethod](pidtagattachmethod-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_RENDERING_POSITION** ([PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md))  <br/> |Read/write  <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

