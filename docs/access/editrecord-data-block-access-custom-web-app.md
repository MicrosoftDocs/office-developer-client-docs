---
title: "EditRecord Data Block (Access custom web app)" 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer 
localization_priority: Normal
ms.assetid: 54975434-78b2-4010-b2f9-f277831fa92e
description: "You can use the EditRecord data block to change the values contained in an existing record."
---

# EditRecord Data Block (Access custom web app)

You can use the **EditRecord** data block to change the values contained in an existing record. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
> [!NOTE]
> The **EditRecord** data block is available only in Data Macros. 
  
## Setting

The **EditRecord** data block has the following arguments. 
  
|**Argument**|**Description**|
|:-----|:-----|
|**Alias** <br/> |A string that identifies the record to edit. If the  *Alias*  argument is not specified, then the current record is edited.  <br/> |
   
## Remarks

After the **EditRecord** statement, you can insert a block of commands that will execute before the changes to the record are committed. The following actions are available in an **EditRecord** data block. 
  
||
|:-----|
|[CancelRecordChange Macro Action](cancelrecordchange-macro-action-access-custom-web-app.md) <br/> |
|[Comment Macro Statement](comment-macro-block-access-custom-web-app.md) <br/> |
|[Group Macro Statement](group-macro-block-access-custom-web-app.md) <br/> |
|[If...Then...Else Macro Statement](ifthenelse-macro-block-access-custom-web-app.md) <br/> |
|[SetField Macro Action](setfield-macro-action-access-custom-web-app.md) <br/> |
|[SetLocalVar Macro Action](setlocalvar-macro-action-access-custom-web-app.md) <br/> |
   
Use the **SetField** action to specify the new values of a field in the edited record. 
  
You can use an **If...Then...Else** statement to perform operations based on a condition. 
  
To cancel the editing of a record, use the **CancelRecordChange** action. This prevents the changes from being committed and exits the **EditRecord** data block. 
  
You can use the **LastCreateRecordIdentity** local variable to work with last record created in a **CreateRecord** data block. For example, use the following syntax to refer to the AssignedTo field of the most recently created record: 
  
`[LastCreateRecordIdentity].[AssignedTo]`


