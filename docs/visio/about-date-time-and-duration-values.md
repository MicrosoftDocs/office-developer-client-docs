---
title: "About Date, Time, and Duration Values"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251852
 
ms.localizationpriority: medium
ms.assetid: b6951a92-f32a-5829-5e07-b277b7934df3
description: "You can perform operations in formulas using date, time, and duration values. In Microsoft Visio, a date and time expression can be evaluated as a single value. A date and time expression is any expression commonly recognized as a date and/or time or a reference to a cell containing a date and/or time. This includes strings and numbers that look like a date and time, and date and time values returned from functions."
---

# About Date, Time, and Duration Values

You can perform operations in formulas using date, time, and duration values. In Microsoft Visio, a date and time expression can be evaluated as a single value. A date and time expression is any expression commonly recognized as a date and/or time or a reference to a cell containing a date and/or time. This includes strings and numbers that look like a date and time, and date and time values returned from functions.
  
Date and time values in Visio are stored internally as a 64-bit floating point number. The value to the left of the decimal represents the number of days since December 30, 1899. The value to the right of the decimal represents the fraction of a day since midnight. Noon is represented by .5.
  
To use dates and times within an expression (rather than as a single constant), you must use the appropriate function to identify them as date and time values.
  
## Valid dates

||||
|:-----|:-----|:-----|
| "2/28"  <br/> | "2/28/99"  <br/> | "2/28/1999"  <br/> |
| "2-28"  <br/> | "2-28-99"  <br/> | "2-28/1999"  <br/> |
| "6 Mar 99"  <br/> | "6 Mar"  <br/> | "6 Mar 99"  <br/> |
| "1 January 99"  <br/> | "Jan 1, 99"  <br/> | "Jan 1, 1999"  <br/> |
| "Jan 00"  <br/> | "January, 2000"  <br/> | "Jan 1, 00"  <br/> |
   
## Valid times

||||
|:-----|:-----|:-----|
| "3:45"  <br/> | "3:45:27"  <br/> | "7a"  <br/> |
| "7 am"  <br/> | "7 p"  <br/> | "7:30 PM"  <br/> |
   
## Date and time functions

|**Function**|**Description**|
|:-----|:-----|
|[DATE](date-function-visioshapesheet.md) <br/> | Converts numbers to a date value. |
|[DATETIME](datetime-function.md) <br/> | Converts a string to a date and time value. |
|[DATEVALUE](datevalue-function-visioshapesheet.md) <br/> | Converts a string to a date value. |
|[NOW](now-function-visioshapesheet.md) <br/> | Returns the current system date as a date and time value. |
|[TIME](time-function-visioshapesheet.md) <br/> | Converts numbers to a time value. |
|[TIMEVALUE](timevalue-function-visioshapesheet.md) <br/> | Converts a string to a time value. |
|[DAY](day-function-visioshapesheet.md) <br/> | Returns the day component in a date and time expression. |
|[DAYOFYEAR](dayofyear-function.md) <br/> | Returns the sequential day of the year in a date and time expression. |
|[HOUR](hour-function-visioshapesheet.md) <br/> | Returns the hours component in a date and time expression. |
|[MINUTE](minute-function-visioshapesheet.md) <br/> | Returns the minutes component in a date and time expression. |
|[MONTH](month-function-visioshapesheet.md) <br/> | Returns the month component in a date and time expression. |
|[SECOND](second-function-visioshapesheet.md) <br/> | Returns the seconds component in a date and time expression. |
|[WEEKDAY](weekday-function-visioshapesheet.md) <br/> | Returns the number of the weekday in a date and time expression. |
|[YEAR](year-function-visioshapesheet.md) <br/> | Returns the year component in a date and time expression. |
   
## Duration

You can perform operations that calculate duration or elapsed time. Duration is stored internally as days and the fraction of a day. For example, 1 elapsed week, 7 elapsed days, and 168 elapsed hours all are stored internally as 7.0, but are displayed with the appropriate units.
  
Visio recognizes the units of duration in the following table.
  
|**Unit**|**Abbreviation**|**Universal abbreviation**|
|:-----|:-----|:-----|
| elapsed day  <br/> | eday, ed. | ed  <br/> |
| elapsed hour  <br/> | ehour, eh. | eh  <br/> |
| elapsed minute  <br/> | eminute, em. | em  <br/> |
| elapsed second  <br/> | esecond, es. | es  <br/> |
| elapsed week  <br/> | eweek, ew. | ew  <br/> |
   
You can add a date and time to a duration to calculate a new date and time. You can perform the operations listed in this table using dates, times, and durations.
  
|**Input**|**Result**|
|:-----|:-----|
| Date-time +/- duration  <br/> | Date and time value  <br/> |
| Duration +/- date-time  <br/> | Date and time value  <br/> |
| Duration +/- duration  <br/> | Duration value  <br/> |
| Date-time + date-time  <br/> | Date and time value  <br/> |
| Date-time - date-time  <br/> | Duration value  <br/> |
   

