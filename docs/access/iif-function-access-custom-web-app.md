---
title: "IIf function (Access custom web app)"
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference 
ms.localizationpriority: medium
ms.assetid: 58a24f46-c61d-432a-a957-d831e960795d
description: "Checks whether a condition is met, and returns one value if TRUE of another on if it is FALSE."
---

# IIf function (Access custom web app)

Checks whether a condition is met, and returns one value if TRUE of another on if it is FALSE.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices.
  
## Syntax

**IIf** (*Condition*, *TrueValue*, *FalseValue*)
  
The **IIf** function contains the following arguments.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Condition*  <br/> |The expression that you want to evaluate.  <br/> |
| *TrueValue*  <br/> |Value or expression returned if *Condition*  is True.  <br/> |
| *FalseValue*  <br/> |Value or expression returned if *Condition*  is False.  <br/> |

## Example

The following expression can be used to display the full name of a person where the table contains FirstName, MiddleInitial, and LastName fields. If the MiddleInitial field is blank, only the FirstName and LastName fields are combined to display the full name.
  
`IIf([MiddleInitial] Is Null,Concat([FirstName]," ",[LastName]),Concat([FirstName]," ",[MiddleInitial]," ",[LastName]))`
