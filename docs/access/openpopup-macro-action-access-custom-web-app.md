---
title: "OpenPopup Macro Action (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 850de802-e417-4884-8d14-571de52aa391
description: "Opens the specified view in a popup window."
---

# OpenPopup Macro Action (Access custom web app)

Opens the specified view in a popup window.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 **OpenPopup** (  *View*  ,  *Where=*  ,  *Order By*  ) 
  
The **OpenPopup** action contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *View*  <br/> |The name of the view to open.  <br/> |
| *Where=*  <br/> |A valid SQL WHERE clause (without the word WHERE) that restricts the records in the view.  <br/> |
| *Order By*  <br/> |A string expression that includes the name of the field or fields on which to sort records and the optional ASC or DESC keywords. By default, this argument is blank.  <br/> |
   
## Remarks

The current macro ends once the **OpenPopup** action is processed. 
  
Any sorting or filtering applied by the user is cleared when the **OpenPopup** action is called. 
  
The  *OrderBy*  argument is the name of the field or fields on which you want to sort records. When you use more than one field name, separate the names with a comma (,). 
  
When you set the  *OrderBy*  argument, the records are sorted by default in ascending order. 
  

