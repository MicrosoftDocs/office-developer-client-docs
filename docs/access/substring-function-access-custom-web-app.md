---
title: "SubString Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
  
ms.localizationpriority: medium
ms.assetid: ae99a0fa-76c4-4c07-9ae9-a7abce23394f
description: "Returns part of a text expression."
---

# SubString Function (Access custom web app)

Returns part of a text expression.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 **SubString** (*TextExpression*, *Start*, *Length*) 
  
The **SubString** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *TextExpression*  <br/> |A text expression.  <br/> |
| *Start*  <br/> |An integer expression that specifies where the returned characters start. If start is less than 1, the returned expression will begin at the first character that is specified in expression. In this case, the number of characters that are returned is the largest value of either the sum of start + length- 1 or 0. If start is greater than the number of characters in the value expression, a zero-length expression is returned.  <br/> |
| *Length*  <br/> |A positive integer expression that specifies how many characters of the expression will be returned. If length is negative, an error is generated and the statement is terminated. If the sum of start and length is greater than the number of characters in expression, the whole value expression beginning at start is returned.  <br/> |
   

