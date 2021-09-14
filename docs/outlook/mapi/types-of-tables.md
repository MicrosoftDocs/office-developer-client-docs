---
title: "Types of Tables"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a1fc4f20-511f-4721-8f09-ec2a5fd0ccb0
description: "Last modified: March 09, 2015"
 
 
---

# Types of Tables

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
There are many different types of tables, each type differentiated by the information that it presents. Tables enable client applications and service providers to readily access and manipulate the important properties of many types of objects. 
  
Some tables, such as contents tables, provide an alternative way of accessing properties. For example, a client can retrieve the subject of a message — its **PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md)) property — either directly from the message by calling its [IMAPIProp::GetProps](imapiprop-getprops.md) method or through the message's contents table. Other tables provide the only way to access object properties. For example, a client cannot access an attachment's **PR_ATTACH_METHOD** ([PidTagAttachMethod](pidtagattachmethod-canonical-property.md)) property by calling **IMAPIProp::GetProps**; it must always retrieve the attachment table of the message to which it is attached. **PR_ATTACH_METHOD** is a required column in all attachment tables. 
  
A table view can be static or dynamic. With a static table view, changes to the underlying data do not cause the view to be updated. Once the view has been instantiated, it does not change. Users of static tables can be informed of changes to data through table notifications. A dynamic table view is updated when changes are made to the data. There are two types of dynamic tables: one that updates the columns of each row, but the rows remain static and one that updates both the columns and rows. This latter type of table always reflects the underlying data exactly.
  
Tables have a default column set, the minimum set of columns that a client or service provider can expect to see when retrieving rows from a table that has not yet been affected by an [IMAPITable::SetColumns](imapitable-setcolumns.md) call. Clients and service providers can add columns to or remove columns from this default set by calling the **SetColumns** method. Changes can be made either statically or dynamically, following a client request. Not all tables support dynamic column set modification. 
  
The MAPI tables and their implementers and users are:
  
|**Table**|**Implementers**|
|:-----|:-----|
|Attachment  <br/> |Implemented by message store providers. Used by clients and transport providers.  <br/> |
|Contents  <br/> |Implemented by message store and address book providers. Used by clients.  <br/> |
|Display  <br/> |Implemented by MAPI and service providers. Used by MAPI and service providers.  <br/> |
|Hierarchy  <br/> |Implemented by message store and address book providers. Used by clients.  <br/> |
|Message service  <br/> |Implemented by MAPI. Used by clients.  <br/> |
|Message store  <br/> |Implemented by MAPI. Used by clients.  <br/> |
|One-off  <br/> |Implemented by address book providers. Used by MAPI.  <br/> |
|Outgoing queue  <br/> |Implemented by message store providers. Used by MAPI spooler.  <br/> |
|Profile  <br/> |Implemented by MAPI. Used by clients.  <br/> |
|Provider  <br/> |Implemented by MAPI. Used by clients.  <br/> |
|Receive folder  <br/> |Implemented by message store providers. Used by clients.  <br/> |
|Recipient  <br/> |Implemented by message store providers. Used by clients and transport providers.  <br/> |
|Status  <br/> |Implemented by MAPI and service providers. Used by clients.  <br/> |
   
## See also



[MAPI Tables](mapi-tables.md)

