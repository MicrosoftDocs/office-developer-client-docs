---
title: "/ (Divide) (Access custom web app)"
  
  
manager: lindalu
ms.date: 09/05/2017
ms.audience: Developer
 
  
ms.localizationpriority: medium
ms.assetid: 3d296730-197b-44db-853b-881597dd9b48
description: "Divides one number by another."
---

# / (Divide) (Access custom web app)

Divides one number by another.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Syntax

 *dividend*  /  *divisor*
  
 *dividend* Is the numeric expression to divide. Can be any valid expression of any one of the data types of the numeric data type category, except the datetime data type.
  
 *Divisor* Is the numeric expression by which to divide the dividend. Can be any valid expression of any one of the data types of the numeric data type category, except the datetime data type.
  
## Return Type

Returns the data type of the argument with the higher precedence.
  
If an integer *dividend* is divided by an integer *divisor*, the result is an integer that has any fractional part of the result truncated.
  
## Remarks

The actual value returned by the / operator is the quotient of the first expression divided by the second expression.
  