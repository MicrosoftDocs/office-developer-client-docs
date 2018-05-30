---
title: "IS [NOT] NULL (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: b941a0c7-9753-4920-bb6d-cbba94ba9422
description: "Determines whether a specified expression is NULL."
---

# IS [NOT] NULL (Access custom web app)

Determines whether a specified expression is NULL.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 *expression* **IS** [  *NOT*  ] **NULL**
  
The **IS [NOT] NULL** predicate contains the following arguments. 
  
|||
|:-----|:-----|
| *expression*  <br/> |Any valid expression.  <br/> |
| *NOT*  <br/> |Specifies that the Boolean result be negated. The predicate reverses its return values, returning TRUE if the value is not NULL, and FALSE if the value is NULL.  <br/> |
   
## Remarks

If the value of  *expression*  is NULL, IS NULL returns TRUE; otherwise, it returns FALSE. 
  
If the value of expression is NULL, IS NOT NULL returns FALSE; otherwise, it returns TRUE.
  

