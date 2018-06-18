---
title: "About the Sample Wrapped PST Store Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 953391ce-31a2-3271-365a-284cf5e15d82
description: "Last modified: July 03, 2012"
 
 
---

# About the Sample Wrapped PST Store Provider

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
## Overview of Message Store Providers

Message store providers handle the storage and retrieval of messages and other information for the users of client applications. The message information is organized by using a hierarchical system known as a message store. The message store is implemented in multiple levels, with containers called folders that hold messages of different types. There is no limit to the number of levels in a message store; folders can contain many subfolders.
  
Message store data can be used in a variety of ways. In addition to the typical email usage, folders can be used as a forum for public discussion, as a repository for reference documents, or as a container for bulletin board information. A single message store can hold many types of information, some modifiable and some not. Multiple clients can install the same message store, making it easy and fast to share data.
  
Message store folders allow you to sort and filter messages and to customize the view in a user interface (UI) display. Links to filtered messages are held in special folders called search-results folders. The user of a client application enters filtering criteria, which MAPI refers to as a restriction, and the criteria is applied to the messages stored in one or more folders. For example, a user might want to view only those messages dealing with a particular subject with arrival dates that are more recent than last week. References to the messages that match the criteria are listed in the search-results folder and the real messages remain in their regular folders.
  
Messages are the units of data transferred from one user or application to another user or application. Every message contains some message text and message envelope information that is used for transmission. Some messages include one or more attachments, or additional data related to and transported with a message in the form of a file, another message, or an OLE object.
  
## The Sample Wrapped PST Store Provider

The Replication API allows you to replicate items from a back-end data repository into an Outlook PST store. You use the Replication API to replicate the data into a dedicated PST store and keep track of the synchronization state. This approach does not require you to introduce a custom MAPI store provider, which is complex to write and maintain. However, the PST store provider does need to be wrapped to work with the Replication API.
  
The Sample Wrapped PST Store Provider uses the Personal Folders file (PST) provider as the back end for storing data. The wrapped PST store provider should be used in conjunction with the Replication API. For more information, see [About the Replication API](about-the-replication-api.md). Most of the functions in the Sample Wrapped PST Store Provider pass their arguments directly to the underlying PST provider. Certain functions require special implementation and are described in the following topics.
  
## In this section

- [Installing the Sample Wrapped PST Store Provider](installing-the-sample-wrapped-pst-store-provider.md)
    
- Explains how to download and install the Sample Wrapped PST Store Provider.
    
- [Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md)
    
- The first step in implementing a wrapped PST store provider is to initialize and configure the wrapped PST store provider.
    
- [Logging On to a Wrapped PST Store Provider](logging-on-to-a-wrapped-pst-store-provider.md)
    
- After a wrapped PST store provider is initialized, you must implement functions so that MAPI and the MAPI spooler can log on to the wrapped PST store provider.
    
- [Using a Wrapped PST Store Provider](using-a-wrapped-pst-store-provider.md)
    
- To use a wrapped PST store provider you must wrap the **[IMAPISupport::IUnknown](imapisupportiunknown.md)** interface to implement common wrapped PST store provider tasks. 
    
- [Shutting Down a Wrapped PST Store Provider](shutting-down-a-wrapped-pst-store-provider.md)
    
- After you finish using a wrapped PST store provider, you must properly shut down the wrapped PST store provider.
    
## See also



[About the Replication API](about-the-replication-api.md)
  
[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

