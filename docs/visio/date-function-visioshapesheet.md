---
title: "DATE Function (VisioShapeSheet)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251412
 
ms.localizationpriority: medium
ms.assetid: 2b6c5375-c543-ff2f-f20a-6d92fd65717a
description: "Returns the date represented by year, month, and day formatted according to the short date style in the system's Regional Settings. The values for year, month, and day reflect the Gregorian calendar."
---

# DATE Function (VisioShapeSheet)

Returns the date represented by  *year, month,*  and  *day*  formatted according to the short date style in the system's Regional Settings. The values for *year*, *month*, and *day* reflect the Gregorian calendar.
  
## Syntax

DATE(***year***, ***month***, ***day***)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *year* <br/> |Required  <br/> |**Integer** <br/> |The year. |
| *month* <br/> |Required  <br/> |**Integer** <br/> |The month. |
| *day* <br/> |Required  <br/> |**Integer** <br/> |The day. |

## Example 1

DATE(1999,6,7)
  
Returns the value representing 6/7/1999.
  
## Example 2

DATE(1999,6,7) + 4 ed.
  
Returns the value representing 6/11/1999.
  
## Example 3

FORMAT(DATE(1999,10,14),"C")
  
Returns the value representing Tuesday, October 14, 1999.
  