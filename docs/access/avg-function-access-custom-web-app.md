---
title: "Avg Function (Access custom web app)"
  
  
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: d432e823-a255-4860-9c8b-201b2e0476fd
description: "Calculates the arithmetic mean of a set of values contained in a specified field."
---

# Avg Function (Access custom web app)

Calculates the arithmetic mean of a set of values contained in a specified field.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 **Avg** (*NumericExpression*) 
  
The **Avg** function contains the following argument. 
  
|**Argument**|**Description**|
|:-----|:-----|
|NumericExpression  <br/> |A string expression identifying the field that contains the numeric data you want to average or an expression that performs a calculation using the data in that field. Operands in  *NumericExpression*  can include the name of a table field, a variable, or a function (which can be either intrinsic or user-defined but not one of the other SQL aggregate functions).  <br/> |
   
## Remarks

The average calculated by **Avg** is the arithmetic mean (the sum of the values divided by the number of values). You could use **Avg**, for example, to calculate average freight cost. 
  
The **Avg** function does not include any **Null** values in the calculation. 
  

