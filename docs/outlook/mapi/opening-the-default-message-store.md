---
title: "Opening the default message store"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 670fb896-9aaf-4a96-83f7-76237409e956
description: "Last modified: July 23, 2011"
---

# Opening the default message store

**Applies to**: Outlook 
  
In any particular session, one message store acts as the default message store. A default message store has the following characteristics:
  
- The **PR_DEFAULT_STORE** ([PidTagDefaultStore](pidtagdefaultstore-canonical-property.md)) property is set to TRUE.
    
- The STATUS_DEFAULT_STORE flag is set in the **PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) property.
    
- MAPI automatically creates the IPM subtree and the root folders for search-results, common views and personal views when the message store is opened. For more information about these folders, see [IPM Subtree](ipm-subtree.md) and [MAPI Special Folders](mapi-special-folders.md). 
    
To retrieve the entry identifier for the default message store, you must call [IMAPISession::GetMsgStoresTable](imapisession-getmsgstorestable.md) to open the message store table and apply an appropriate restriction in a call to [HrQueryAllRows](hrqueryallrows.md). **HrQueryAllRows** will return a row set with the one row that represents the default message store. The restriction that you pass to **HrQueryAllRows** can take on one of the following forms: 
  
1. An **AND** restriction that uses an **SAndRestriction** structure to combine: 
    
   - An exists restriction that uses an **SExistRestriction** structure to test for the existence of the **PR_DEFAULT_STORE** property. 
    
   - A property restriction that uses an [SPropertyRestriction](spropertyrestriction.md) structure to check for the TRUE value in the **PR_DEFAULT_STORE** property. 
    
2. A bitmask restriction that uses an [SBitMaskRestriction](sbitmaskrestriction.md) structure for applying STATUS_DEFAULT_STORE as a mask against the **PR_RESOURCE_FLAGS** property. 
    
## See also

- [SExistRestriction](sexistrestriction.md)
- [SAndRestriction](sandrestriction.md)

