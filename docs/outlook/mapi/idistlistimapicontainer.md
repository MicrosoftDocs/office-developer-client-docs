---
title: "IDistList  IMAPIContainer"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IDistList
api_type:
- COM
ms.assetid: bd8e1ddb-3027-428b-8964-81614f80282d
description: "Last modified: March 09, 2015"
---

# IDistList : IMAPIContainer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to distribution lists in modifiable address book containers. **IDistList** can create, copy, and delete distribution lists, in addition to performing name resolution. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Distribution list objects  <br/> |
|Implemented by:  <br/> |Address book providers  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IDistList  <br/> |
|Pointer type:  <br/> |LPDISTLIST  <br/> |
|Transaction model:  <br/> |Transacted  <br/> |
   
## Vtable order

This interface does not have any unique methods.
  
|**Required properties**|**Access**|
|:-----|:-----|
|**PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
   
## Remarks

The **IDistList** interface inherits from [IMAPIContainer](imapicontainerimapiprop.md) and includes the same methods as address book containers. Therefore, because the methods of the **IDistList** interface are identical to those of the [IABContainer](iabcontainerimapicontainer.md) interface, they are not duplicated here. 
  
A distribution list or object that implements **IDistList** is a collection of messaging user objects, or individual recipients. A distribution list can consist of all messaging user objects, or some messaging user and some distribution lists. 
  
There are typically two types of distribution lists:
  
- Distribution lists that are expanded by the underlying messaging system. This type of list has an address, **PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md)), and is treated the same as if it were an individual recipient. 
    
- Distribution lists that exist in a local container and are expanded by the client application.
    
Optional distribution list properties include the following:
  
- **PR_LAST_MODIFICATION_TIME** ([PidTagLastModificationTime](pidtaglastmodificationtime-canonical-property.md))
    
- **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md)) 
    
- **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) 
    
Notice that **PR_ADDRTYPE** is required, but **PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) is not. That is because a distribution list without an email address can still receive messages, but its member list must be expanded. If the **PR_ADDRTYPE** property is set to MAPIPDL, MAPI performs the expansion. If **PR_ADDRTYPE** is a value other than MAPIPDL, the transport provider performs the expansion. 
  
For additional information about how to use the **IDistList** methods, see the reference entries for the parallel methods of **IABContainer**.
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

