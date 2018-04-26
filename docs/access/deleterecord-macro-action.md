---
title: "DeleteRecord Macro Action"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: c656a72c-c037-76a5-dc07-f6eccb6590dd
description: "You can use the DeleteRecord action to delete a record."
---

# DeleteRecord Macro Action

You can use the **DeleteRecord** action to delete a record. 
  
## Setting

The **CreateRecord** data block has the following arguments. 
  
|**Argument**|**Description**|
|:-----|:-----|
|**Record Alias** <br/> |A string that identifies the record to delete. If the  *Alias*  argument is not specified, then the current record is deleted.  <br/> |
   
## Remarks

You can use the **LastCreateRecordIdentity** local variable to work with last record created in a **CreateRecord** data block. For example, use the following syntax to refer to the most recently created record: 
  
```
[LastCreateRecordIdentity]
```


