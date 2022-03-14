---
title: "CreateRecord Data Block (Access custom web app)" 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer 
ms.localizationpriority: medium
ms.assetid: 9dd73bae-a8d5-4d8b-b356-01ac72f7e5d9
description: "You can use the CreateRecord data block to create a new record in the specified table."
---

# CreateRecord Data Block (Access custom web app)

You can use the **CreateRecord** data block to create a new record in the specified table. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices. 
  
> [!NOTE]
> The **CreateRecord** data block is available only in Data Macros. 
  
## Setting

The **CreateRecord** data block has the following arguments. 
  
The **CreateRecord** data block has the following arguments. 
  
|**Argument name**|**Required**|**Description**|
|:-----|:-----|:-----|
|**Create a Record In** <br/> |Yes  <br/> |The name of the table to create the new record in. |
|**Alias** <br/> |No  <br/> |A string that identifies the record. You can use the record's alias to identify  <br/> |
   
## Remarks

The record created by **CreateRecord** automatically becomes the current record. 
  
After **CreateRecord** statement, you can insert a block of commands that will execute before the new record is committed. The following actions are available in a **CreateRecord** data block. 
  
|Action |
|:-----|
|[CancelRecordChange Macro Action](cancelrecordchange-macro-action-access-custom-web-app.md) <br/> |
|[Comment Macro Statement](comment-macro-block-access-custom-web-app.md) <br/> |
|[Group Macro Statement](group-macro-block-access-custom-web-app.md) <br/> |
|[If...Then...Else Macro Statement](ifthenelse-macro-block-access-custom-web-app.md) <br/> |
|[SetField Macro Action](setfield-macro-action-access-custom-web-app.md) <br/> |
|[SetLocalVar Macro Action](setlocalvar-macro-action-access-custom-web-app.md) <br/> |
   
After the **CreateRecord** action creates a record, use the **SetField** action to specify a value of a field in the new record. 
  
You can use an **If...Then...Else** statement to perform operations based on a condition. 
  
To cancel the creation of a record, use the **CancelRecordChange** action. This prevents the changes from being committed and exits the **CreateRecord** data block. 
  
Once the new record is committed, you can use the **LastCreateRecordIdentity** local variable to work with the record. For example, use the following syntax to refer to the AssignedTo field of the most recently created record. 
  
`[LastCreateRecordIdentity].[AssignedTo]`


