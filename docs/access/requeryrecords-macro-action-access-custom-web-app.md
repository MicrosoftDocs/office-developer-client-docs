---
title: "RequeryRecords Macro Action (Access custom web app)"
 
 
manager: lindalu
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
ms.localizationpriority: medium
ms.assetid: 1dab102f-24af-4984-8020-a9fb06355639
description: "You can use the RequeryRecords action to refresh, sort, and filter the data in the active view by requerying the source of the view."
---

# RequeryRecords Macro Action (Access custom web app)

You can use the **RequeryRecords** action to refresh, sort, and filter the data in the active view by requerying the source of the view.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Setting

The **RequeryRecords** action has the following arguments.
  
|**Parameter**|**Required**|**Description**|
|:-----|:-----|:-----|
|**Where=** <br/> |No  <br/> |A SQL WHERE clause that restricts the records in the view. By default, this argument is blank. |
|**OrderBy** <br/> |No  <br/> |A string expression that includes the name of the field or fields on which to sort records and the optional ASC or DESC keywords. By default, this argument is blank. |

## Remarks

Any sorting or filtering applied by the user is cleared when the **RequeryRecords** action is called.
  
The *OrderBy* argument is the name of the field or fields on which you want to sort records. When you use more than one field name, separate the names with a comma (,).
  
When you set the *OrderBy* argument, the records are sorted by default in ascending order.
  
To sort records in descending order, enter DESC at the end of the *OrderBy* argument expression. For example, to sort customer records in descending order by contact name, set the *OrderBy* argument to "ContactName DESC".
  
To sort names by LastName descending, and FirstName ascending, set the *OrderBy* argument to "LastName DESC, FirstName ASC".
  