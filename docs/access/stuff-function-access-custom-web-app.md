---
title: "Stuff Function (Access custom web app)"
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 4d8d6a34-f884-40a4-b330-5c104d16cf97
description: "Inserts a text string into another text string. It deletes a specified length of characters in the first string at the start position and then inserts the second string into the first string at the start position."
---

# Stuff Function (Access custom web app)

Inserts a text string into another text string. It deletes a specified length of characters in the first string at the start position and then inserts the second string into the first string at the start position.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Syntax

 **Stuff** (*IntoTextExpression*, *Start*, *Length*, *ThisTextExpression*)
  
The **Stuff** function contains the following arguments.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *IntoTextExpression*  <br/> |A text expression that specifies the text into which the text specified by the *ThisTextExpression* will be inserted.  <br/> |
| *Start*  <br/> |An integer value that specifies the location to start deletion and insertion. If start or length is negative, a null string is returned. If start is longer than the first *IntoTextExpression*, a null string is returned.  <br/> |
| *Length*  <br/> |An integer that specifies the number of characters to delete. If length is longer than the first *IntoTextExpression*, deletion occurs up to the last character in the last *IntoTextExpression*.  <br/> |
| *ThisTextExpression*  <br/> |A text expression hat specifies the text to insert into *IntoTextExpression*. This expression will replace length characters of *IntoTextExpression*  beginning at *Start*.  <br/> |

## Remarks

If the *Start* or *Length* arguments are negative, or if the starting position is larger than length of the first string, a null string is returned. If the start position is 0, a null value is returned. If the length to delete is longer than the first string, it is deleted to the first character in the first string.
  