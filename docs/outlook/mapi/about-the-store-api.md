---
title: "About the Store API"
description: "The Store API provides miscellaneous store functionality to store providers. This article describes related definitions, data types, properties, and interfaces."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 166a8e60-e09d-7473-b61b-35d78a863192
 
 
---

# About the Store API

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The Store API provides miscellaneous store functionality to store providers. It provides the following defintions, data types, properties, and interfaces.
  
Definitions:
  
- [Constants for the Store API](mapi-constants.md)
    
Data types:
  
- **[INDEX_SEARCH_PUSHER_PROCESS](index_search_pusher_process.md)**
    
- **[MSCAP_SELECTOR](mscap_selector.md)**
    
Named Properties:
  
- **[ArchiveSourceSupportMask](archivesourcesupportmask.md)**
    
- **[CrawlSourceSupportMask](crawlsourcesupportmask.md)**
    
- **[Display Server Folder Sizes](display-server-folder-sizes-property.md)**
    
- **[Hide Meeting Update Option](hide-meeting-update-option-property.md)**
    
- **[Make Store Type Private](make-store-type-private-property.md)**
    
- **[NoFolderScan](nofolderscan.md)**
    
> [!NOTE]
> Store providers that do not require any of the functionality offered by these named properties can simply ignore them and not implement support in the **IMAPIProp** interface. Because these properties are provided starting in Microsoft Outlook 2003 Service Pack 1, adding them to a store in an earlier version of Microsoft Outlook has no effect. They are ignored if they do not exist or if their value is **false**. 
  
Properties:
  
- **[PR_ADDITIONAL_REN_ENTRYIDS](pidtagadditionalrenentryids-canonical-property.md)**
    
- **[PR_PROVIDER_ITEMID](pidtagprovideritemid-canonical-property.md)**
    
- **[PR_PROVIDER_PARENT_ITEMID](pidtagproviderparentitemid-canonical-property.md)**
    
- **[PR_SEARCH_OWNER_ID](pidtagsearchownerid-canonical-property.md)**
    
Interfaces:
  
- **[IFolderSupport](ifoldersupportiunknown.md)**
    
- **[IMSCapabilities](imscapabilitiesiunknown.md)**
    
- **[IProxyStoreObject](iproxystoreobject.md)**
    
## Registering Stores for Indexing

The MAPI Protocol Handler checks the Windows registry for stores that it should index for search purposes. Store providers that want to be indexed must be registered in the Windows registry. For more information about registering store providers for indexing in Outlook 2013 or Outlook 2010, see [About Registering Stores for Indexing](about-registering-stores-for-indexing.md).
  
## Indexing Stores

MAPI store providers can choose to allow the MAPI Protocol Handler to crawl and index messages in the store, or send notifications to the indexer only when there are messages to be indexed. For more information about notifications-based indexing, see [About Notification-Based Store Indexing](about-notification-based-store-indexing.md).
  

