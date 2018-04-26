---
title: "OR (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e7190523-87cf-4e04-aef4-d229776cd16b
description: "Combines two conditions. Returns TRUE when either of the two conditions is true."
---

# OR (Access custom web app)

Combines two conditions. Returns TRUE when either of the two conditions is true.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 *BooleanExpression* **Or** *BooleanExpression* 
  
The **Or** operator uses the following argument. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *BooleanExpression*  <br/> |Any valid expression that returns TRUE or FALSE.  <br/> |
   
## Remarks

When more than one logical operator is used in a statement, **Or** operators are evaluated after **And** operators. However, you can change the order of evaluation by using parentheses. 
  
The following table shows the result of the **Or** operator. 
  
||**TRUE**|**FALSE**|
|:-----|:-----|:-----|
|**TRUE** <br/> |TRUE  <br/> |TRUE  <br/> |
|**FALSE** <br/> |TRUE  <br/> |FALSE  <br/> |
   

