---
title: "Round Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 4af7fbe2-ee34-4a52-b55e-ce3983313b5e
description: "Returns a numeric value, either rounded or truncated, to the specified length or precision."
---

# Round Function (Access custom web app)

Returns a numeric value, either rounded or truncated, to the specified length or precision.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 **Round** (  *Number*  ,  *Precision*  , [  *TruncateInsteadOfRound*  ]) 
  
The **Round** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Number*  <br/> |A numeric expression.  <br/> |
| *Precision*  <br/> |The precision to which  *Number*  is to be rounded.  *Precision*  must be a numeric expression. When  *Precision*  is a positive number,  *Number*  is rounded to the number of decimal positions specified by length. When  *Precision*  is a negative number,  *Number*  is rounded on the left side of the decimal point, as specified by length.  <br/> |
| *TruncateInsteadOfRound*  <br/> |The type of operation to perform. When omitted or set to 0,  *Number*  is rounded. When a value other than 0 is specified,  *Number*  is truncated. The default value is 0.  <br/> |
   
## Remarks

 **Round** always returns a value. If length is negative and larger than the number of digits before the decimal point, **Round** returns 0. 
  

