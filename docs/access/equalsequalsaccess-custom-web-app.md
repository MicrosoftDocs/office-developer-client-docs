---
title: "Equals(Access custom web app)"
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 70bc707a-3a61-4d75-816d-0defd0806319
description: "Compares the equality of two expressions."
---

# Equals (Access custom web app)

Compares the equality of two expressions.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

`= (Equals)`

*expression*  =  *expression* 
  
*expression*  Is any valid expression. If the expressions are not of the same data type, the data type for one expression must be implicitly convertible to the data type of the other. The conversion depends on the rules of data type precedence. 
  
## Return Type

**Boolean**
  
## Remarks

When you compare two NULL expressions, the result is TRUE.
  
Comparing NULL to a non-NULL value always results in FALSE.
  

