---
title: "NOW Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251470
 
ms.localizationpriority: medium
ms.assetid: 96cac1f6-cc17-466f-23d8-a9006e7de05f
description: "Returns the current date and time value."
---

# NOW Function (VisioShapeSheet)

Returns the current date and time value.
  
## Syntax

NOW ( )
  
### Return value

Datetime
  
## Remarks

NOW is automatically recalculated every minute. 
  
## Example 1

NOW( )
  
Returns the current date and time, such as 9/27/2010 12:03:30 PM.
  
## Example 2

FORMAT(NOW(),"dd MMM., yyyy hh:mm")
  
Returns the current date and time formatted as 27 Sep., 2010 12:03.
  
## Example 3

NOW()+2EW.
  
Returns the current date and time plus two elapsed weeks, such as 10/11/10 12:03:30 PM.
  

