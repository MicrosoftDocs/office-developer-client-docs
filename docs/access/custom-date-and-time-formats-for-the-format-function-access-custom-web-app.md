---
title: "Custom date and time formats for the Format function (Access custom web app)" 
manager: kelbow
ms.date: 08/18/2017
ms.audience: Developer
localization_priority: Normal
ms.assetid: f7d15fe6-bdad-4f1f-aa18-12a21fc111c4
description: "Learn how to control how a date or time is displayed by creating a custom formatting."
---

# Custom date and time formats for the Format function (Access custom web app)

Learn how to control how a date or time is displayed by creating a custom formatting.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Format specifications

The following table lists characters you can use with the [Format Function (Access custom web app)](format-function-access-custom-web-app.md) function to create custom date and time formats. 
  
|**Format specification**|**Description**|
|:-----|:-----|
|(:)  <br/> |Time separator. In some locales, other characters may be used to represent the time separator. The time separator separates hours, minutes, and seconds when time values are formatted. The actual character that is used as the time separator in formatted output is determined by your application's current culture value.  <br/> |
|(/)  <br/> |Date separator. In some locales, other characters may be used to represent the date separator. The date separator separates the day, month, and year when date values are formatted. The actual character that is used as the date separator in formatted output is determined by your application's current culture.  <br/> |
|(%)  <br/> |Used to indicate that the following character should be read as a single-letter format without regard to any trailing letters. Also used to indicate that a single-letter format is read as a user-defined format. See what follows for additional details.  <br/> |
|d  <br/> |Displays the day as a number without a leading zero (for example, 1). Use %d if this is the only character in your user-defined numeric format.  <br/> |
|dd  <br/> |Displays the day as a number with a leading zero (for example, 01).  <br/> |
|ddd  <br/> |Displays the day as an abbreviation (for example, Sun).  <br/> |
|dddd  <br/> |Displays the day as a full name (for example, Sunday).  <br/> |
|M  <br/> |Displays the month as a number without a leading zero (for example, January is represented as 1). Use %M if this is the only character in your user-defined numeric format.  <br/> |
|MM  <br/> |Displays the month as a number with a leading zero (for example, 01/12/01).  <br/> |
|MMM  <br/> |Displays the month as an abbreviation (for example, Jan).  <br/> |
|MMMM  <br/> |Displays the month as a full month name (for example, January).  <br/> |
|gg  <br/> |Displays the period/era string (for example, A.D.).  <br/> |
|h  <br/> |Displays the hour as a number without leading zeros using the 12-hour clock (for example, 1:15:15 PM). Use %h if this is the only character in your user-defined numeric format.  <br/> |
|hh  <br/> |Displays the hour as a number with leading zeros using the 12-hour clock (for example, 01:15:15 PM).  <br/> |
|H  <br/> |Displays the hour as a number without leading zeros using the 24-hour clock (for example, 1:15:15). Use %H if this is the only character in your user-defined numeric format.  <br/> |
|HH  <br/> |Displays the hour as a number with leading zeros using the 24-hour clock (for example, 01:15:15).  <br/> |
|m  <br/> |Displays the minute as a number without leading zeros (for example, 12:1:15). Use %m if this is the only character in your user-defined numeric format.  <br/> |
|mm  <br/> |Displays the minute as a number with leading zeros (for example, 12:01:15).  <br/> |
|s  <br/> |Displays the second as a number without leading zeros (for example, 12:15:5). Use %s if this is the only character in your user-defined numeric format.  <br/> |
|ss  <br/> |Displays the second as a number with leading zeros (for example, 12:15:05).  <br/> |
|f  <br/> |Displays fractions of seconds. For example ff displays hundredths of seconds, whereas ffff displays ten-thousandths of seconds. You may use up to seven f symbols in your user-defined format. Use %f if this is the only character in your user-defined numeric format.  <br/> |
|t  <br/> |Uses the 12-hour clock and displays an uppercase A for any hour before noon; displays an uppercase P for any hour between noon and 11:59 P.M. Use %t if this is the only character in your user-defined numeric format.  <br/> |
|tt  <br/> |For locales that use a 12-hour clock, displays an uppercase AM with any hour before noon; displays an uppercase PM with any hour between noon and 11:59 P.M.  <br/> For locales that use a 24-hour clock, displays nothing.  <br/> |
|y  <br/> |Displays the year number (0-9) without leading zeros. Use %y if this is the only character in your user-defined numeric format.  <br/> |
|yy  <br/> |Displays the year in two-digit numeric format with a leading zero, if applicable.  <br/> |
|yyy  <br/> |Displays the year in four-digit numeric format.  <br/> |
|yyyy  <br/> |Displays the year in four-digit numeric format.  <br/> |
||Displays the timezone offset without a leading zero (for example, -8). Use %z if this is the only character in your user-defined numeric format.  <br/> |
|z  <br/> |Displays the timezone offset with a leading zero (for example, -08).  <br/> |
|zz  <br/> |Displays the timezone offset with a leading zero (for example, -08)  <br/> |
|zzz  <br/> |Displays the full timezone offset (for example, -08:00)  <br/> |
   
## Remarks

Formatting strings are case-sensitive. Different formatting can be obtained by using a different case. For example, when formatting a date value with the string "D" you get the date in the long format (according to your current locale). However, if you change the case to "d" you get the date in the short format. Also, unexpected results or an error might occur if the intended formatting does not match the case of any defined format string.
  
## See also

- [Format function (Access custom web app)](format-function-access-custom-web-app.md) 
- [Custom numeric formats for the Format function (Access custom web app)](custom-numeric-formats-for-the-format-function-access-custom-web-app.md)
  

