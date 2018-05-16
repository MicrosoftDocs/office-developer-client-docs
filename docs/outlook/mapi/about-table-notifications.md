---
title: "About Table Notifications"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 00c9c6c2-fc21-4b9c-91fa-629450a22d37
description: "Last modified: July 23, 2011"
 
 
---

# About Table Notifications

  
  
**Applies to**: Outlook 
  
Clients often rely on table notifications to learn of changes to objects instead of registering to receive notifications directly from the objects. Typical changes that cause notifications to be sent include the addition, deletion, or modification of a row and any critical error. When notifications arrive, clients can determine whether to make another call to reload the table. 
  
Because table notifications are asynchronous, there are a few issues that can make handling notifications less than straightforward:
  
- The data passed in the [TABLE_NOTIFICATION](table_notification.md) structure might not represent the table's most current state. For example, a client might make a change to a message and then decide to delete it. The message store provider implementing the contents table that included the message sends two notifications: a TABLE_ROW_MODIFIED event followed by a TABLE_ROW_DELETED event. Depending on how the message store provider times notifications, the client might receive the TABLE_ROW_MODIFIED notification after the deletion of the row. 
    
- The column set included with a notification might be different from the table's current column set. MAPI requires that the notification column set match the column set that was in effect at the time that the notification was generated. Because it is possible for a client to call [IMAPITable::SetColumns](imapitable-setcolumns.md) to alter the column set at any time — including after a notification — the two column sets may not be synchronized. 
    
- Table notifications are only sent for rows that are part of the view. That is, if a row is excluded from the view due to a restriction or because the table is in a collapsed state, no notification will be sent if that row changes. Also, no notifications are sent to inform a client about a change in category state.
    
Clients should be aware that not all tables support the TABLE_SORT_DONE notification and should be prepared to handle this condition by:
  
1. Forcing the sort to be synchronous.
    
2. Reloading the rows of the table when [IMAPITable::SortTable](imapitable-sorttable.md) returns. 
    
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

