---
title: "Sending or receiving a message on demand"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 479404c5-4926-402a-aa12-75dd23276d75
---

# Sending or receiving a message on demand
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Clients typically rely on the MAPI subsystem — the MAPI spooler and the service providers — to handle the timing of message transmission and reception. However, you can alter this timing by using the status object of either the MAPI spooler or a transport provider.
  
The [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md) method removes all messages from one or more transport provider's incoming or outgoing queues. The following procedures describe two techniques for sending or receiving messages on demand. The first procedure uses the MAPI spooler's status object to flush the queues of every transport provider in the profile; the second procedure flushes the queue of a single transport provider. 
  
### To flush all incoming or outgoing queues in a single operation
  
1. Call [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to access the status table. 
    
2. Call the status table's [IMAPITable::SetColumns](imapitable-setcolumns.md) method to limit the column set to **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) and **PR_RESOURCE_TYPE** ([PidTagResourceType](pidtagresourcetype-canonical-property.md)).
    
3. Build a property restriction using an [SPropertyRestriction](spropertyrestriction.md) structure to match **PR_RESOURCE_TYPE** with MAPI_SPOOLER. 
    
4. Call [HrQueryAllRows](hrqueryallrows.md), passing in the **SPropertyRestriction** structure, to retrieve the row that represents the status of the MAPI spooler. 
    
5. Pass the **PR_ENTRYID** column to [IMAPISession::OpenEntry](imapisession-openentry.md) to open the MAPI spooler's status object. 
    
6. Call the MAPI spooler's [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md) method, passing the FLUSH_NO_UI flag to suppress the user interface and either the FLUSH_DOWNLOAD or FLUSH_UPLOAD flag to flush the outgoing or incoming queues. 
    
7. Release the status object and the status table, as well as the [SRowSet](srowset.md) structure that is allocated for the table. 
    
### To flush incoming or outgoing queues individually by transport provider
  
1. Call [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to access the status table. 
    
2. Call the status table's [IMAPITable::SetColumns](imapitable-setcolumns.md) method to limit the column set to **PR_ENTRYID** and **PR_RESOURCE_TYPE**.
    
3. Build a property restriction using an [SPropertyRestriction](spropertyrestriction.md) structure to match **PR_RESOURCE_TYPE** with MAPI_TRANSPORT_PROVIDER. 
    
4. Call [HrQueryAllRows](hrqueryallrows.md), passing in the **SPropertyRestriction** structure, to retrieve the rows that are supplied by transport providers. 
    
5. For each row returned from **HrQueryAllRows**:
    
    1. Pass the **PR_ENTRYID** column to [IMAPISession::OpenEntry](imapisession-openentry.md) to open the transport provider's status object. 
        
    2. Check that the transport status object supports the **FlushQueues** method by checking that its **PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md)) property has the STATUS_FLUSH_QUEUES flag set. 
        
    3. If supported, call [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md). If unsupported, call the MAPI spooler's **IMAPIStatus::FlushQueues** method, passing the entry identifier of the transport in the _lpTargetTransport_ parameter. See the preceding procedure for instructions on accessing the MAPI spooler's status object. Set the FLUSH_DOWNLOAD flag to flush the outgoing queues or the FLUSH_UPLOAD flag to flush the incoming queues. 
        
    4. Release the status object and the status table, as well as the [SRowSet](srowset.md) structure that is allocated for the table. 
    
The MAPI spooler honors the FLUSH_NO_UI flag as do most LAN transport providers. However, not all transport providers honor this flag, particularly those that use a modem explicitly and the Remote Access Service (RAS). RAS was not designed to allow clients to suppress the user interface. It is possible for a client to be configured so that it can connect without requiring the interaction of a user, but it is difficult and requires intimate knowledge of the client's message services.
  

