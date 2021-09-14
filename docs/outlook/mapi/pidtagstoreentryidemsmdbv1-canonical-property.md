---
title: "PidTagStoreEntryIdEmsmdbV1 Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 40161358-4d41-43cf-83c7-fdd843bec87b
description: "Last modified: March 09, 2015"
---

# PidTagStoreEntryIdEmsmdbV1 Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the old style (Microsoft Outlook 2002 and earlier versions) of the entry identifier of a Microsoft Exchange Server 2010 or Exchange Server 2013 message store.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_STORE_ENTRYID_EMSMDB_V1  <br/> |
|Identifier:  <br/> |0x65F60102  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |ID properties  <br/> |
   
## Remarks

Starting with Microsoft Outlook 2003, the server FQDNs were integrated into the entry IDs, thereby avoiding additional RPCs for referrals. However, this makes entry IDs longer and introduces more scenarios where the **CompareEntryIDs** method must be used to determine whether two entry IDs are equivalent. The PR_STORE_ENTRYID_EMSMDB_V1 (PidTagStoreIdEmsbdbV1) property accesses the older format of the Exchange Server entry ID used by Microsoft Outlook 2002 (Microsoft Office XP) and earlier versions. This can save space and also reduce the number of **CompareEntryIDs** calls needed to determine when entry IDs are equivalent. Note that using the older entry IDs to open a mailbox may incur some additional RPCs if a referral is required. 
  
To access the PR_STORE_ENTRYID_EMSMDB_V1 property while in cached mode, you must bypass the cache using the MAPI_NO_CACHE flag with the [IMAPIProp::GetProps](imapiprop-getprops.md) method. If **PR_STORE_ENTRYID_EMSMDB_V1** isn't available, the code should fall back to PR_STORE_ENTRYID. Only Outlook 2003 through Microsoft Outlook 2013 support the PR_STORE_ENTRYID_EMSMDB_V1 property. 
  
## See also



[PidTagStoreEntryId Canonical Property](pidtagstoreentryid-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

