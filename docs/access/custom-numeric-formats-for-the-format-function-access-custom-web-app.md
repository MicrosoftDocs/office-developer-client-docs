---
title: "Custom numeric formats for the Format function (Access custom web app)"
manager: kelbow
ms.date: 8/18/2017
ms.audience: Developer 
localization_priority: Normal
ms.assetid: 97efe972-d873-47d7-be81-8ae3461870c4
description: "Learn how to control how a number is displayed by creating a user-defined number format."
---

# Custom numeric formats for the Format function (Access custom web app)

Learn how to control how a number is displayed by creating a user-defined number format.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 

You can change the way a number is displayed by creating a user-defined number format. A user-defined number format can have from one to three sections separated by a semicolon (;). If the Style argument of the [Format Function (Access custom web app)](format-function-access-custom-web-app.md) function contains one of the predefined numeric formats, only one section is allowed. 
  
## Format specifications
<a name="bk_addresources"> </a>

The following table lists characters you can use to create user-defined number formats.
  
|**Format specification**|**Description**|
|:-----|:-----|
|None  <br/> |Displays the number without formatting.  <br/> |
|**0** (zero character)  <br/> |Digit placeholder. Displays a digit or a zero. If the expression has a digit in the position where the zero appears in the format string, displays the digit; otherwise, displays a zero in that position.  <br/> If the number has fewer digits than there are zeros (on either side of the decimal) in the format expression, displays leading or trailing zeros. If the number has more digits to the right side of the decimal separator than there are zeros to the right side of the decimal separator in the format expression, rounds the number to as many decimal places as there are zeros. If the number has more digits to the left of the decimal separator than there are zeros to the left of the decimal separator in the format expression, displays the additional digits without modification.  <br/> |
|#  <br/> |Digit placeholder. Displays a digit or nothing. If the expression has a digit in the position where the # character appears in the format string, displays the digit; otherwise, displays nothing in that position.  <br/> This symbol works exactly like the 0 digit placeholder, except that leading and trailing zeros aren't displayed if the number has fewer digits than there are # characters on either side of the decimal separator in the format expression.  <br/> |
|. (dot character)  <br/> |Decimal placeholder. The decimal placeholder determines how many digits are displayed to the left and right of the decimal separator. If the format expression contains only # characters to the left of this symbol; numbers smaller than 1 begin with a decimal separator. To display a leading zero displayed with fractional numbers, use zero as the first digit placeholder to the left of the decimal separator. In some locales, a comma is used as the decimal separator. The actual character that is used as a decimal placeholder in the formatted output depends on the number format recognized by the system. Thus, you should use the period as the decimal placeholder in your formats even if you are in a locale that uses a comma as a decimal placeholder. The formatted string will appear in the format correct for the locale.  <br/> |
|%  <br/> |Percent placeholder. Multiplies the expression by 100. The percent character (%) is inserted in the position where it appears in the format string.  <br/> |
|, (comma character)  <br/> |Thousand separator. The thousand separator separates thousands from hundreds in a number that has four or more places to the left of the decimal separator. Standard use of the thousand separator is specified if the format contains a thousand separator enclosed in digit placeholders (0 or #).  <br/> A thousand separator immediately to the left of the decimal separator (whether a decimal is specified) or as the rightmost character in the string means "scale the number by dividing it by 1,000, rounding as needed." Numbers smaller than 1,000 but greater or equal to 500 are displayed as 1, and numbers smaller than 500 are displayed as 0. Two adjacent thousand separators in this position scale by a factor of 1 million, and an additional factor of 1,000 for each additional separator.  <br/> Multiple separators in any position other than immediately to the left of the decimal separator or the rightmost position in the string are treated only as specifying the use of a thousand separator. In some locales, a period is used as a thousand separator. The actual character that is used as the thousand separator in the formatted output depends on the Number Format recognized by the system. Thus, you should use the comma as the thousand separator in your formats even if you are in a locale that uses a period as a thousand separator. The formatted string will appear in the format correct for the locale.  <br/> For example, consider the three following format strings:  <br/> "#,0.", which uses the thousands separator to format the number 100 million as the string "100,000,000".  <br/> "#0,.", which uses scaling by a factor of one thousand to format the number 100 million as the string "100000".  <br/> "#,0,.", which uses the thousands separator and scaling by one thousand to format the number 100 million as the string "100,000".  <br/> |
|: (colon character)  <br/> |Time separator. In some locales, other characters may be used to represent the time separator. The time separator separates hours, minutes, and seconds when time values are formatted. The actual character that is used as the time separator in formatted output is determined by the system settings.  <br/> |
|/ (forward slash character)  <br/> |Date separator. In some locales, other characters may be used to represent the date separator. The date separator separates the day, month, and year when date values are formatted. The actual character that is used as the date separator in formatted output is determined by the system settings.  <br/> |
|**E- , E+ , e- , e+** <br/> |Scientific format. If the format expression contains at least one digit placeholder (0 or #) to the left of E-, E+, e-, or e+, the number is displayed in scientific format and E or e is inserted between the number and its exponent. The number of digit placeholders to the left determines the number of digits in the exponent. Use E- or e- to place a minus sign next to negative exponents. Use E+ or e+ to place a minus sign next to negative exponents and a plus sign next to positive exponents. You must also include digit placeholders to the right side of this symbol to achieve correct formatting.  <br/> |
|**- + $ ( )** <br/> |Literal characters. These characters are displayed exactly as typed in the format string. To display a character other than one of those listed, precede it with a backslash (\) or enclose it in double quotation marks (" ").  <br/> |
|\ (backward slash character)  <br/> |Displays the next character in the format string. To display a character that has special meaning as a literal character, precede it with a backslash (\). The backslash itself isn't displayed. By using a backslash is the same as enclosing the next character in double quotation marks. To display a backslash, use two backslashes (\\).  <br/> Examples of characters that can't be displayed as literal characters are the date-formatting and time-formatting characters (a, c, d, h, m, n, p, q, s, t, w, y, /, and :), the numeric-formatting characters (#, 0, %, E, e, comma, and period), and the string-formatting characters (@, &amp;, \<, \>, and !).  <br/> |
|"ABC"  <br/> |Displays the string inside the double quotation marks (" "). To include a string in the style argument within code, you must use Chr(34) to enclose the text (34 is the character code for a quotation mark (")).  <br/> |
   
The following table contains some sample format expressions for numbers. (These examples all assume that your system's locale setting is English-U.S.) The first column contains the format strings for the Format function. The other columns contain the resulting output if the formatted data has the value given in the column headings.
  
|**Format (Style)**|**"5" formatted as**|**"-5" formatted as**|**"0.5" formatted as**|**"0" formatted as**|
|:-----|:-----|:-----|:-----|:-----|
|Zero-length string ("")  <br/> |5  <br/> |-5  <br/> |0.5  <br/> |0  <br/> |
|0  <br/> |5  <br/> |-5  <br/> |1  <br/> |0  <br/> |
|0.00  <br/> |5.00  <br/> |-5.00  <br/> |0.50  <br/> |0.00  <br/> |
|#,##0  <br/> |5  <br/> |-5  <br/> |1  <br/> |0  <br/> |
|$#,##0;($#,##0)  <br/> |$5  <br/> |($5)  <br/> |$1  <br/> |$0  <br/> |
|$#,##0.00;($#,##0.00)  <br/> |$5.00  <br/> |($5.00)  <br/> |$0.50  <br/> |$0.00  <br/> |
|0%  <br/> |500%  <br/> |-500%  <br/> |50%  <br/> |0%  <br/> |
|0.00%  <br/> |500.00%  <br/> |-500.00%  <br/> |50.00%  <br/> |0.00%  <br/> |
|0.00E+00  <br/> |5.00E+00  <br/> |-5.00E+00  <br/> |5.00E-01  <br/> |0.00E+00  <br/> |
|0.00E-00  <br/> |5.00E00  <br/> |-5.00E00  <br/> |5.00E-01  <br/> |0.00E00  <br/> |
|"$#,##0;;\Z\e\r\o"  <br/> |$5  <br/> |$-5  <br/> |$1  <br/> |Zero  <br/> |
   
## Remarks
<a name="bk_addresources"> </a>

If you include semicolons with nothing between them, the missing section is displayed by using the format of the positive value.
  
## See also

- [Format Function (Access custom web app)](format-function-access-custom-web-app.md) 
- [Custom date and time formats for the Format function (Access custom web app)](custom-date-and-time-formats-for-the-format-function-access-custom-web-app.md)
  

