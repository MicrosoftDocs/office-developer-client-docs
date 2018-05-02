---
title: "About Format Pictures"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251831
 
localization_priority: Normal
ms.assetid: df4c1c70-8b41-c046-7415-643188af0e06
description: "A format picture is used to determine how a value is displayed. For example, you can control the number of digits displayed to the right or left of a decimal point, or whether a text string appears as uppercase or lowercase."
---

# About Format Pictures

A format picture is used to determine how a value is displayed. For example, you can control the number of digits displayed to the right or left of a decimal point, or whether a text string appears as uppercase or lowercase.
  
> [!NOTE]
> To define a date or time format picture by using Microsoft Office system formatting, enclose the format picture in double curly braces , for example, "{{m/d/yy}}". If you are using a predefined format, for example, 201, enclose it in curly braces and angle brackets, like this: "{\<201\>}" 
  
The following sections show symbols you can use to format different types of values for display.
  
## String and numeric values

|**Character**|**Description**|
|:-----|:-----|
|#  <br/> |Digit placeholder. Displays either a digit or nothing. Leading and trailing zeros are not displayed. If more digits than placeholders are to the left of the decimal, all digits are displayed. If more digits than placeholders are to the right of the decimal, the fraction is rounded to the number of placeholders. For a dimension, if the placeholder is the leftmost digit, subunits that are 0 are not displayed.  <br/> For example, FORMAT(0ft 11.25in,"#.##u") displays 11.25in.  <br/> |
|0  <br/> |Digit placeholder (zero). Displays either a digit or nothing. Leading and trailing zeros are displayed. If more digits than placeholders are to the left of the decimal, all digits are displayed. If more digits than placeholders are to the right of the decimal, the fraction is rounded to the number of placeholders. For a dimension, subunits that are 0 are displayed.  <br/> For example, FORMAT(2ft 11.33in,"0.## u") displays 2 ft. 11.33 in.  <br/> |
|.  <br/> |Decimal placeholder. Determines how many digits are displayed to the left and right of the decimal position. In a multipart unit, the decimal is used in the smallest (rightmost) subunit. Displays the decimal character defined for the system's **Region and Language** settings (Control Panel).  <br/> For example, FORMAT(250 cm,"0.000 u") displays 250.000 cm.  <br/> |
|,  <br/> |Thousands separator. If surrounded by digit placeholders (# or 0), the separator separates thousands from hundreds within a number that has four or more digits to the left of the decimal. Displays the thousands separator defined for the system's **Region and Language** settings (Control Panel).  <br/> |
|E- E+ e- e+  <br/> |Scientific format. If the format contains at least one digit placeholder to the right of these symbols, the number is displayed in scientific format. Inserts the E or e between the number and its exponent. For E+ or e+, displays the plus (+) sign before positive exponents and the minus (-) sign before negative exponents. For E- or e-, displays the minus (-) sign only when the exponent is negative.  <br/> For example, FORMAT(12345.67,"###.#e+#") displays 123.5e+2.  <br/> |
|u or U  <br/> |Short label placeholder. Inserts abbreviated unit labels after each subunit. For example: in., ft., deg. The U placeholder inserts mixed-case labels, while the u placeholder inserts lowercase labels. Inserts the same number of spaces before the label as before the placeholder.  <br/> For example, FORMAT(12 c 13 d,"#u") displays 13c1.  <br/> |
|uu or UU  <br/> |Long label placeholder. Inserts unit labels after each subunit. For example: inches, feet, degrees The U placeholder inserts mixed-case labels, while the u placeholder inserts lowercase labels. Inserts the same number of spaces before the label as before the placeholder.  <br/> For example, FORMAT(12.43in,"# #/4 UU") displays 12 2/4 INCHES.  <br/> |
|uuu or UUU  <br/> |Universal label placeholder. Inserts the universal (internal to Visio) form of unit labels after each subunit. The U placeholder inserts mixed-case labels, while the u placeholder inserts lowercase labels. Inserts the same number of spaces before the label as before the placeholder.  <br/> |
|/  <br/> |Fraction placeholder. Displays expression as a whole number with fraction if a leading digit placeholder is present. Otherwise, displays only the whole number in the numerator. If a number follows the digit placeholder in the denominator, rounds the fraction to the nearest fraction whose numerator is 1 and simplifies it. If a number is specified in the denominator without the digit placeholder, rounds to the nearest fraction but does not simplify it.  <br/> For example, FORMAT(12.43,"# #/4") displays 12 2/4.  <br/> |
|space  <br/> |Displays a space character in the formatted output. To display another character, use the backslash (\) character.  <br/> |
   
## Currency values

|**Character**|**Description**|
|:-----|:-----|
|$  <br/> |Currency symbol. Displays the currency symbol defined for the system's **Region and Language** settings (Control Panel)  <br/> |
|u or U  <br/> |Short label placeholder. Inserts the standard symbol for local currency or the three-character currency abbreviations for nonlocal currencies. For example, $99.00, 42.70 FRF. The u placeholder inserts lowercase, and U inserts mixed-case labels.  <br/> |
|uu or UU  <br/> |Long label placeholder. Inserts long currency labels after each subunit. For example: U.S. dollar, French franc. The u placeholder inserts lowercase, and U inserts mixed-case labels.  <br/> |
|uuu or UUU  <br/> |Universal label placeholder. Inserts the universal, three-character currency abbreviations for all currencies after each subunit. For example, 99.00 USD, 42.70 FRF. The u placeholder inserts lowercase, and U inserts mixed-case labels. Inserts the same number of spaces before the label as before the placeholder.  <br/> |
   
## Text values

|**Character**|**Description**|
|:-----|:-----|
|\  <br/> |Displays the next character as is. To display the backslash character, type \\. See also "text".  <br/> |
|"text" or 'text'  <br/> |Displays the text enclosed in quotation marks as is. See also \ (backslash).  <br/> |
|@  <br/> |Text placeholder. Replaces a string if the value of an expression is a string.  <br/> For example, FORMAT("Hello", "'You entered ('@')'" ) results in "You entered (Hello)".  <br/> |
|@+  <br/> |Uppercase text placeholder. For string values, substitutes the input with uppercase.  <br/> For example, FORMAT("Hello", "@ @+ @-" ) results in "Hello HELLO hello)".  <br/> |
|@-  <br/> |Text placeholder. For string values, substitutes the input with lowercase.  <br/> For example, FORMAT("Hello", "@ @+ @-" ) results in "Hello HELLO hello)".  <br/> |
   
## Date values

|**Character**|**Description**|
|:-----|:-----|
|c or C  <br/> |Date or time placeholder. Displays date and time values using a short (c) or long (C) date format, and the general time format. Visio versions 4.0 and earlier ignore this placeholder.  <br/> For example: FORMAT(DATETIME("6/25/07 12:05"),"C") displays Monday, June 25, 2007 12:05:00 PM. FORMAT(DATETIME("Jun. 25, 2007"),"c") displays 6/25/2007.  <br/> |
|/  <br/> |Date separator. If the expression is a date, separates the date components. Displays the date separator defined for the system's **Region and Language** settings (Control Panel).  <br/> |
| [ ]  <br/> |Elapsed date placeholder. Used with the d, dd, w, and ww placeholders to display duration units.  <br/> For example, [d] or [dd] is elapsed days and [w] or [ww] is elapsed weeks.  <br/> |
|d  <br/> |Day placeholder. Displays the day as a number (1-31) without a leading zero.  <br/> |
|dd  <br/> | Day placeholder. Displays the day as a number (01-31) with a leading zero.  <br/> |
|ddd or w  <br/> |Short day of week placeholder. Displays the day as an abbreviation (Sun-Sat).  <br/> |
|dddd or w  <br/> |Long day of week placeholder. Displays the day as a full name (Sunday-Saturday).  <br/> |
|ddddd  <br/> |Short date placeholder. Displays a date in the short form defined for the system's **Region and Language** settings (Control Panel).  <br/> |
|dddd  <br/> |Long date placeholder. Displays a date in the long form defined for the system's **Region and Language** settings (Control Panel).  <br/> |
|D  <br/> |Day placeholder for Traditional Chinese. Displays the day of the month as the textual representation of the ordinal number. Locale-specific.  <br/> |
|D_c  <br/> |Day placeholder for Traditional Chinese. Displays the day of the month as the textual representation of the ordinal number. Independent of the user locale.  <br/> |
|w_c or w_c  <br/> |Day placeholder for Traditional Chinese. Independent of the user locale.  <br/> |
|w_e  <br/> |Short day of week placeholder for English. Displays the day as an abbreviation (Sun-Sat). Independent of the user locale.  <br/> |
|w_j  <br/> |Short day of week placeholder for Japanese. Displays the day as an abbreviation. Independent of the user locale.  <br/> |
|w_k  <br/> |Short day of week placeholder for Korean. Displays the day as an abbreviation. Independent of the user locale.  <br/> |
|w_s or w_s  <br/> |Day placeholder for Simplified Chinese. Independent of the user locale.  <br/> |
|ww_e  <br/> |Long day of week placeholder for English. Displays the day as a full name (Sunday-Saturday). Independent of the user locale.  <br/> |
|ww_j  <br/> |Long day of week placeholder for Japanese. Displays the day as a full name. Independent of the user locale.  <br/> |
|w_k  <br/> |Long day of week placeholder for Korean. Displays the day as a full name. Independent of the user locale.  <br/> |
|M  <br/> |Month placeholder. Displays the month as a number (1-12) without a leading zero. See also m (minute placeholder).  <br/> |
|MM  <br/> |Month placeholder. Displays the month as a number (01-12) with a leading zero. See also mm (minute placeholder).  <br/> |
|MMM  <br/> |Month placeholder. Displays the month in abbreviated form (Jan-Dec).  <br/> |
|MMMM  <br/> |Month placeholder. Displays the full name of the month (January-December).  <br/> |
|MMMM_c  <br/> |Month placeholder for Traditional Chinese. Displays the full name of the month. Independent of the user locale.  <br/> |
|MMMM_e  <br/> |Month placeholder for English. Displays the full name of the month. Independent of the user locale.  <br/> |
|yy  <br/> |Year placeholder. Displays the year as a two-digit number (00-99).  <br/> |
|yyyy  <br/> |Year placeholder. Displays the year as a four-digit number (1900-2078).  <br/> |
|g  <br/> |Year placeholder. Locale-specific. For Japanese, displays short version for Gengo era. For Korean, displays Korean year label followed by a space.  <br/> |
|g_j  <br/> |Year placeholder. For Japanese, displays short version for Gengo era. Independent of user locale.  <br/> |
|gg or G  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays short version for formal year label. For Japanese, displays short version for Gengo era in Kanji. For Korean, displays Korean year label followed by a space.  <br/> |
|gg_c  <br/> |Year placeholder. For Traditional Chinese, displays short version for formal year label. Independent of user locale.  <br/> |
|gg_j  <br/> |Year placeholder. For Japanese, displays short version for Gengo era in Kanji. Independent of user locale.  <br/> |
|gg_k  <br/> |Year placeholder. For Korean, displays Korean year label followed by a space. Independent of user locale.  <br/> |
|ggg or GG  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays full version for formal year label. For Japanese, displays full version for Gengo era in Kanji. For Korean, displays Korean year label followed by a space.  <br/> |
|ggg_c  <br/> |Year placeholder. For Traditional Chinese, displays full version for formal year label. Independent of user locale.  <br/> |
|ggg_j  <br/> |Year placeholder. For Japanese, displays full version for Gengo era in Kanji. Independent of user locale.  <br/> |
|e  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays string representing the Julian year. For Japanese, displays Gengo year as one or two digits and no leading zero. For Korean, displays the Korean year as a four-digit Arabic numeral.  <br/> |
|e_c  <br/> |Year placeholder. For Traditional Chinese, displays string representing the Julian year. Independent of user locale.  <br/> |
|e_j  <br/> |Year placeholder. For Japanese, displays Gengo year as a one- or two-digit Arabic numeral. Independent of user locale.  <br/> |
|e_k  <br/> |Year placeholder. For Korean, displays the Korean year as a four-digit Arabic numeral. Independent of user locale.  <br/> |
|E  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays a string representing the republic year. For Japanese, displays Gengo year as one or two digits and no leading zero. For Korean, displays the Korean year as a four-digit Arabic numeral.  <br/> |
|E_c  <br/> |Year placeholder. For Traditional Chinese, displays a string representing the republic year. Independent of user locale.  <br/> |
|ee  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays string representing the Julian year. For Japanese, displays Gengo year as a two-digit Arabic numeral with leading zero if needed. For Korean, displays the Korean year as a four-digit Arabic numeral.  <br/> |
|ee_j  <br/> |Year placeholder. For Japanese, displays Gengo year as a two-digit Arabic numeral. Independent of user locale.  <br/> |
|EE  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays a string representing the republic year. For Japanese, displays Gengo year as a two-digit Arabic numeral with leading zero if needed. For Korean, displays the Korean year as a four-digit Arabic numeral.  <br/> |
|n or N  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays the republic year as an Arabic numeral. For Japanese, displays Gengo year as one or two digits and no leading zero. For Korean, displays the Korean year as a four-digit Arabic numeral.  <br/> |
|n_c  <br/> |Year placeholder. For Traditional Chinese, displays the republic year as an Arabic numeral. Independent of user locale.  <br/> |
|nn or NN  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays the republic year as an Arabic numeral. For Japanese, displays Gengo year as a two-digit Arabic numeral with leading zero if needed. For Korean, displays the Korean year as a four-digit Arabic numeral.  <br/> |
   
## Time values

|**Character**|**Description**|
|:-----|:-----|
|:  <br/> |Time separator. Displays the time defined for the system's **Region and Language** settings (Control Panel).  <br/> |
|[ ]  <br/> |Elapsed time placeholder. Used with the h, hh, m, mm, s, and ss placeholders to display duration units. For example, [h] or [hh] is elapsed hours, [m] or [mm] is elapsed minutes, and [s] or [ss] is elapsed seconds.  <br/> |
|h  <br/> |Hour placeholder. Displays the hour without a leading zero in 12-hour form (0-12).  <br/> |
|hh  <br/> |Hour placeholder. Displays the hour with a leading zero in 12-hour form (00-12).  <br/> |
|H  <br/> |Hour placeholder. Displays the hour without a leading zero in 24-hour form (0-24).  <br/> |
|HH  <br/> |Hour placeholder. Displays the hour with a leading zero in 24-hour form (00-24).  <br/> |
|m  <br/> |Minute placeholder. Displays the minutes without a leading zero (0-59).  <br/> |
|mm  <br/> |Minute placeholder. Displays the minutes with a leading zero (00-59).  <br/> |
|s  <br/> |Second placeholder. Displays the seconds without a leading zero (0-59).  <br/> |
|ss  <br/> |Second placeholder. Displays the seconds with a leading zero (00-59).  <br/> |
|t  <br/> |AM/PM abbreviation. Displays the abbreviation defined for the system's **Region and Language** settings (Control Panel).  <br/> |
|tt  <br/> |AM/PM designator. Displays the full designator defined for the system's **Region and Language** settings (Control Panel).  <br/> |
|t_c or tt_c  <br/> |Traditional Chinese AM/PM designator. Displays the designator. Independent of user locale.  <br/> |
|t_k or tt_k  <br/> |Korean AM/PM designator. Displays the designator. Independent of user locale.  <br/> |
|t_j or tt_j  <br/> |Japanese AM/PM designator. Displays the designator. Independent of user locale.  <br/> |
|t_e  <br/> |English AM/PM designator. Displays the short designator. Independent of user locale.  <br/> |
|tt_e  <br/> |English AM/PM designator. Displays the full designator. Independent of user locale.  <br/> |
|t_s or tt_s  <br/> |Simplified Chinese AM/PM designator. Displays the designator. Independent of user locale.  <br/> |
|T  <br/> |General time format.  <br/> |
   

