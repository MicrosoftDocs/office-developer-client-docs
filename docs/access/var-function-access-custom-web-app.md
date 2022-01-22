---
title: "Var Function (Access custom web app)"
  
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference  
ms.localizationpriority: medium
ms.assetid: cb2aace1-fa2d-480e-bfc7-44ae399943f5
description: "Returns the statistical variance for a population sample represented as a set of values contained in a specified field in a query."
---

# Var Function (Access custom web app)

Returns the statistical variance for a population sample represented as a set of values contained in a specified field in a query.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Syntax

 **Var** (*NumericExpression*)
  
The **Var** function contains the following argument.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *NumericExpression*  <br/> |A text expression identifying the field that contains the numeric data you want to evaluate or an expression that performs a calculation using the data in that field. Operands in *NumericExpression* can include the name of a table field, a constant, or a function (which can be either intrinsic or user-defined but not one of the other SQL aggregate functions).  <br/> |

## Remarks

 **Var** can be used with numeric columns only. Null values are ignored. 