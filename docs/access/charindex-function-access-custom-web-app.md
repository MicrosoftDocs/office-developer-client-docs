---
title: "CharIndex function (Access custom web app)" 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer 
ms.localizationpriority: medium
ms.assetid: 340ed9a8-6f82-4aa8-a951-2c453b3d1ac4
description: "Searches a text expression for another text expression and returns its starting position if found."
---

# CharIndex function (Access custom web app)

Searches a text expression for another text expression and returns its starting position if found.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Syntax

**CharIndex** (*TextExpression*, *WithinText*, [*Start*])
  
|**Argument Name**|**Required**|**Description**|
|:-----|:-----|:-----|
| *TextExpression*  <br/> |Yes  <br/> |A text expression that contains the text to be found.  <br/> |
| *WithinText*  <br/> |Yes  <br/> |The text expression to be searched.  <br/> |
| *Start*  <br/> |No  <br/> |An integer that specifies the location in *WithinText* to begin the search. If *Start* is not specified, is a negative number, or is 0, the search starts at the beginning of *WithinText*.  <br/> |

## Remarks

If either *TextExpression*  or *WithinText*  is NULL, *CharIndex* returns NULL.
  
If *TextExpression*  is not found within *WithinText*, *CharIndex* returns 0.
  
The starting position returned is 1-based, not 0-based.
  