---
title: "DeleteRecord Data Macro action (Access custom web app)"
manager: lindalu
ms.date: 09/05/2021
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: f6b68a9a-e04a-476e-a407-b1779fea1953
---

# DeleteRecord Data Macro action (Access custom web app)

You can use the **DeleteRecord** action to delete a record. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Setting

The **DeleteRecord** action has the following arguments. 
  
|**Argument**|**Description**|
|:-----|:-----|
|**Record Alias** <br/> |A string that identifies the record to delete. If the  *Alias*  argument is not specified, then the current record is deleted.  <br/> |
   
## Remarks

You can use the **LastCreateRecordIdentity** local variable to work with last record created in a **CreateRecord** data block. For example, use the following syntax to refer to the most recently created record: 
  
`[LastCreateRecordIdentity]`
