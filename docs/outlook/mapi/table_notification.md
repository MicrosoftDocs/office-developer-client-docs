---
title: "TABLE_NOTIFICATION"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.TABLE_NOTIFICATION
api_type:
- COM
ms.assetid: 48e478c4-6e9a-40ab-a7bb-e6219b743b08
description: "Last modified: March 09, 2015"
---

# TABLE_NOTIFICATION

**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a row in a table that has been affected by some type of event, such as a change or an error. This causes a table notification to be generated. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _TABLE_NOTIFICATION
{
  ULONG ulTableEvent;
  HRESULT hResult;
  SPropValue propIndex;
  SPropValue propPrior;
  SRow row;
} TABLE_NOTIFICATION;

```

## Members

**ulTableEvent**
  
> Bitmask of flags used to represent the table event type. The following flags can be set:
    
TABLE_CHANGED 
  
> Indicates at a high level that something about the table has changed. The table's state is as it was before the event. This means that all **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) properties, bookmarks, current positioning, and user interface selections are still valid. Handle this event by rereading the table. Service providers that do not want to implement rich table notifications send TABLE_CHANGED events instead of more detailed events to indicate a particular type of change. 
    
TABLE_ERROR 
  
> An error has occurred, usually during the processing of an asynchronous operation. Errors during the processing of the following methods can generate this event: 
    
   - [IMAPITable::SortTable](imapitable-sorttable.md)
    
   - [IMAPITable::SetColumns](imapitable-setcolumns.md)
    
   - [IMAPITable::Restrict](imapitable-restrict.md)
    
   After receiving a TABLE_ERROR event, a client cannot rely on the accuracy of the table contents. Also, pending notifications about other changes might be lost. The [IMAPITable::GetLastError](imapitable-getlasterror.md) method might not provide any additional information about the error because it was generated at some previous point, not necessarily from the last method call. 
    
TABLE_RELOAD 
  
> The data in the table should be reloaded. Service providers send TABLE_RELOAD when, for example, the underlying data is stored in a database and the database is replaced. Handle this event by assuming that nothing about the table is still valid and by rereading the table. All bookmarks, instance keys, status and positioning information are invalid.
    
TABLE_RESTRICT_DONE 
  
> A restriction operation initiated with an **IMAPITable::Restrict** method call has completed. 
    
TABLE_ROW_ADDED 
  
> A new row has been added to the table and the corresponding object saved. TABLE_ROW_ADDED events are generated after a call to the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. 
    
TABLE_ROW_DELETED 
  
> A row has been removed from the table. The **propPrior** member is set to NULL. 
    
TABLE_ROW_MODIFIED 
  
> A row has been changed. The **row** member contains the affected properties for the row. Multiple TABLE_ROW_MODIFIED events are sent in the order that they appear in the table view. 
    
  TABLE_ROW_MODIFIED events are sent after changes to the corresponding object have been committed with a call to the **IMAPIProp::SaveChanges** method. If the modified row is now the first row in the table, the value of the property tag in the **propPrior** member is **PR_NULL** ([PidTagNull](pidtagnull-canonical-property.md)).
    
TABLE_SETCOL_DONE 
  
> A column setting operation initiated with an **IMAPITable::SetColumns** method call has completed. 
    
TABLE_SORT_DONE 
  
> A table sorting operation initiated with an **IMAPITable::SortTable** method call has completed. 
    
**hResult**
  
> HRESULT value for the error that has occurred, if the **ulTableEvent** member is set to TABLE_ERROR. 
    
**propIndex**
  
> [SPropValue](spropvalue.md) structure for the **PR_INSTANCE_KEY** property of the affected row. 
    
**propPrior**
  
> **SPropValue** structure for the **PR_INSTANCE_KEY** property of the row before the affected one. If the affected row is the first row in the table, **propPrior** must be set to **PR_NULL** and not zero. Zero is not a valid property tag. 
    
**row**
  
> [SRow](srow.md) structure describing the affected row. This structure is filled for all table notification events. For table notification events that do not pass row data, the **cValues** member of the **SRow** structure is set to zero and the **lpProps** member is set to NULL. Because this **SRow** structure is read-only; clients must make a copy of it if they want to make modifications. The [ScDupPropset](scduppropset.md) function can be used to make the copy. 
    
## Remarks

The **TABLE\_NOTIFICATION** structure is one of the members of the union of structures included in the **info** member of the [NOTIFICATION](notification.md) structure. The **info** member includes a **TABLE\_NOTIFICATION** structure when the **ulEventType** member of the structure is set to  _fnevTableModified_.
  
The order and type of columns in the row member reflect the order and type that was in effect at the time that the notification was generated. The order and type at the time that the notification was generated is not necessarily the same as when the notification was delivered. 
  
For more information about notification, see the topics described in the following table.
  
|**Topic**|**Description**|
|:-----|:-----|
|[Event Notification in MAPI](event-notification-in-mapi.md) <br/> |General overview of notification and notification events.  <br/> |
|[Handling Notifications](handling-notifications.md) <br/> |Discussion of how clients should handle notifications.  <br/> |
|[Supporting Event Notification](supporting-event-notification.md) <br/> |Discussion of how service providers can use the **IMAPISupport** method to generate notifications.  <br/> |
   
Because table notifications are asynchronous, clients can receive notification of an added row after learning about the addition through another means. It is possible to receive a TABLE_ERROR event when there is an error in an **IMAPITable::Sort**, **IMAPITable::Restrict**, or **IMAPITable::SetColumns** method or when an underlying process attempts to update a table with, for example, new or modified rows. 
  
## See also

- [NOTIFICATION](notification.md) 
- [ScDupPropset](scduppropset.md)
- [SRow](srow.md)
- [SPropValue](spropvalue.md)
- [MAPI Structures](mapi-structures.md)

