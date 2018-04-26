---
title: "CreateRecord Data Block"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: e18f47f8-2aad-9a14-ad63-ab603a4d5b07
description: "You can use the CreateRecord data block to create a new record in the specified table."
---

# CreateRecord Data Block

You can use the **CreateRecord** data block to create a new record in the specified table. 
  
> [!NOTE]
> The **CreateRecord** data block is available only in Data Macros. 
  
## Setting

The **CreateRecord** data block has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
|**Create a Record In** <br/> |Yes  <br/> |The name of the table to create the new record in.  <br/> |
|**Alias** <br/> |No  <br/> |An string that identifies the record. You can use the record's alias to identify  <br/> |
   
## Remarks

The record created by **CreateRecord** automatically becomes the current record. 
  
After **CreateRecord** statement, you can insert a block of commands that will execute before the new record is committed. The following actions are available in a **CreateRecord** data block. 
  
||
|:-----|
|[CancelRecordChange Macro Action](cancelrecordchange-macro-action.md) <br/> |
|[Comment Macro Statement](comment-macro-statement.md) <br/> |
|[Group Macro Statement](group-macro-statement.md) <br/> |
|[If...Then...Else Macro Statement](ifthenelse-macro-block.md) <br/> |
|[SetField Macro Action](setfield-macro-action.md) <br/> |
|[SetLocalVar Macro Action](setlocalvar-macro-action.md) <br/> |
   
After the **CreateRecord** action creates a record, use the **SetField** action to specify a value of a field in the new record. 
  
You can use an **If...Then...Else** statment to perform operations based on a condition. 
  
To cancel the creation of a record, use the **CancelRecordChange** action. This prevents the changes from being committed and exits the **CreateRecord** data block. 
  
Once the new record is committed, you can use the **LastCreateRecordIdentity** local variable to work with the record. For example, use the following syntax to refer to the AssignedTo field of the most recently created record. 
  
```
[LastCreateRecordIdentity].[AssignedTo]
```

The **CreateRecord** data block can only be used in the **[After Insert](after-insert-macro-event.md)**, **[After Update](after-update-macro-event.md)**, and **[After Update](after-update-macro-event.md)** data macro events. 
  

