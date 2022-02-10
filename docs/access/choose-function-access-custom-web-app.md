---
title: "Choose function (Access custom web app)" 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 70c1ac24-a28f-4401-91d3-61129578bebd
description: "Returns the item at the specified index from a list of values."
---

# Choose function (Access custom web app)

Returns the item at the specified index from a list of values.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Syntax

**Choose** (*IndexNumber*, *Value*, [*Value_n*])
  
The **Choose** function contains the following arguments.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *IndexNumber*  <br/> |An integer expression that represents a 1-based index into the list of the items following it. |
| *Value*  <br/> |List of values of any data type. |

## Remarks

If the provided *IndexNumber* is not an integer, then the value is implicitly converted to an integer.
  
If the index value exceeds the bounds of the array of values, **Choose** returns NULL.
  