---
title: "Count function (Access custom web app)" 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: d931535b-428f-4300-93bf-cfe0ebcc2ac9
description: "Returns the number of records in a query or table."
---

# Count function (Access custom web app)

Returns the number of records in a query or table.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Syntax

**Count** (*Expression*)
  
The **Count** function contains the following argument.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Expression*  <br/> |A string expression identifying the field that contains the data you want to count or an expression that performs a calculation using the data in the field. Operands in *Expression* can include the name of a table field or function (which can be either intrinsic or user-defined but not other SQL aggregate functions). You can count any kind of data, including text.  <br/> |
   
## Remarks

You can use Count to count the number of records in an underlying query. For example, you could use Count to count the number of orders shipped to a particular country or region.
  
**Count** (\*) returns the number of items in a group. This includes NULL values and duplicates.
