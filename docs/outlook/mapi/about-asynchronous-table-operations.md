---
title: "About asynchronous table operations"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 57219d96-bd9e-4e9a-b34a-dd3aad97bfd9
description: "Last modified: March 09, 2015"
---

# About asynchronous table operations
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
The **IMAPITable** interface includes three methods that operate asynchronously and three methods for controlling an asynchronous operation. The following table lists these methods: 
  
|**Asynchronous operation**|**Asynchronous control method**|
|:-----|:-----|
|[IMAPITable::SetColumns](imapitable-setcolumns.md) <br/> |[IMAPITable::GetStatus](imapitable-getstatus.md) <br/> |
|[IMAPITable::Restrict](imapitable-restrict.md) <br/> |[IMAPITable::Abort](imapitable-abort.md) <br/> |
|[IMAPITable::SortTable](imapitable-sorttable.md) <br/> |[IMAPITable::WaitForCompletion](imapitable-waitforcompletion.md) <br/> |
   
**To retrieve status information about a table's type and current operation**
  
- Call [IMAPITable::GetStatus](imapitable-getstatus.md). With **GetStatus**, a table user can determine whether the table is static or dynamic, if an operation is in progress or has completed, and if an error has occurred from a completed operation. For example, if a client needs to cancel a sort operation because it is taking too much time, the client can first call **GetStatus** to determine whether, in fact, a sort operation is presently processing. Then the client can call [IMAPITable::Abort](imapitable-abort.md) to stop it. 
    
**To suspend activity until an asynchronous task has completed**
  
- Call [IMAPITable::WaitForCompletion](imapitable-waitforcompletion.md). Calling **WaitForCompletion** allows the task to complete without interruption. 
    
## See also

- [MAPI Tables](mapi-tables.md)

