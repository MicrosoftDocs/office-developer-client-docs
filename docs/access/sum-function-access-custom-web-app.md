---
title: "Sum Function (Access custom web app)" 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference  
ms.localizationpriority: medium
ms.assetid: c2345092-ba5f-4030-9070-391233e70f92
description: "Returns the sum of all the values in the expression."
---

# Sum Function (Access custom web app)

Returns the sum of all the values in the expression.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
## Syntax

 **Sum** (*NumericExpression*)
  
The **Sum** function contains the following argument.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *NumericExpression*  <br/> |An expression identifying the field that contains the numeric data you want to add or an expression that performs a calculation using the data in that field. Operands in *NumericExpression* can include the name of a table field, a constant, or a function (which can be either intrinsic or user-defined but not one of the other SQL aggregate functions). |

## Remarks

The **Sum** function ignores records that contain Null values.
  
The **Sum** function can only be used with numeric columns.
  