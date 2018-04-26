---
title: "EditRecord Data Block"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: fe9f55eb-d7ed-1914-65a9-fa2fcb332b98
description: "You can use the EditRecord data block to change the values contained in an existing record."
---

# EditRecord Data Block

You can use the **EditRecord** data block to change the values contained in an existing record. 
  
> [!NOTE]
> The **EditRecord** data block is available only in Data Macros. 
  
## Setting

The **EditRecord** data block has the following arguments. 
  
|**Argument**|**Description**|
|:-----|:-----|
|**Alias** <br/> |A string that identifies the record to edit. If the  *Alias*  argument is not specified, then the current record is edited.  <br/> |
   
## Remarks

After **EditRecord** statement, you can insert a block of commands that will execute before the changes to the record are comitted. The following actions are available in a **EditRecord** data block. 
  
||
|:-----|
|[CancelRecordChange Macro Action](cancelrecordchange-macro-action.md) <br/> |
|[Comment Macro Statement](comment-macro-statement.md) <br/> |
|[Group Macro Statement](group-macro-statement.md) <br/> |
|[If...Then...Else Macro Statement](ifthenelse-macro-block.md) <br/> |
|[SetField Macro Action](setfield-macro-action.md) <br/> |
|[SetLocalVar Macro Action](setlocalvar-macro-action.md) <br/> |
   
Use the **SetField** action to specify the new values of a field in the edited record. 
  
You can use an **If...Then...Else** statment to perform operations based on a condition. 
  
To cancel the editing of a record, use the **CancelRecordChange** action. This prevents the changes from being committed and exits the **EditRecord** data block. 
  
You can use the **LastCreateRecordIdentity** local variable to work with last record created in a **CreateRecord** data block. For example, use the following syntax to refer to the AssignedTo field of the most recently created record: 
  
```
[LastCreateRecordIdentity].[AssignedTo]
```

The CreateRecord data block can only be used in the **[After Insert](after-insert-macro-event.md)**, **[After Update](after-update-macro-event.md)**, and **[After Update](after-update-macro-event.md)** data macro events. 
  

