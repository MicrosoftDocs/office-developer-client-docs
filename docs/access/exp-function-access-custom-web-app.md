---
title: "Exp Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
  
ms.localizationpriority: medium
ms.assetid: 09385b75-ec0e-4dde-b9c3-9ade4a7a2b74
description: "Returns the exponential value of the specified expression."
---

# Exp Function (Access custom web app)

Returns the exponential value of the specified expression.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 **Exp** (*NumericExpression*) 
  
The **Exp** function contains the following argument. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *NumericExpression*  <br/> |An expression of type Double or of a type that can be implicitly converted to Double.  <br/> |
   
## Remarks

The constant **e** (2.718281…), is the base of natural logarithms. 
  
The exponent of a number is the constant **e** raised to the power of the number. For example **Exp** (1.0) = e^1.0 = 2.71828182845905 and **Exp** (10) = e^10 = 22026.4657948067. 
  
The exponential of the natural logarithm of a number is the number itself: **Exp** (LOG (n)) = n. And the natural logarithm of the exponential of a number is the number itself: LOG (**Exp** (n)) = n. 
  

