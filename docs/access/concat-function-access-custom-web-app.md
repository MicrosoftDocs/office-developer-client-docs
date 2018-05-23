---
title: "Concat function (Access custom web app)"
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
localization_priority: Normal
ms.assetid: 38ad6365-79df-4342-9b76-ca27b8ab8952
description: "Returns a string that is the result of combining two or more string values."
---

# Concat function (Access custom web app)

Returns a string that is the result of combining two or more string values.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

**Concat** (*Value1*, *Value2*, …[*ValueN*]) 
  
The **Concat** function contains the following arguments. 
  
|**Argument Name**|**Description**|
|:-----|:-----|
|Value  <br/> |A string value to concatenate to the other values.  <br/> |
   
## Remarks

**Concat** takes a variable number of string arguments and concatenates them into a single string. A minimum of two string arguments are required; otherwise, an error is raised. 
  
All arguments are implicitly converted to string data types and then concatenated.
  
## Example

The following expression can be used to display the full name of a person where the table contains FirstName, MiddleInitial, and LastName fields. If the MiddleInitial field is blank, only the FirstName and LastName fields are combined to display the full name.
  
```vb
IIf([MiddleInitial] Is Null,Concat([FirstName]," ",[LastName]),Concat([FirstName]," ",[MiddleInitial]," ",[LastName]))
```


