---
title: "About Format Pictures"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251831
 
ms.localizationpriority: medium
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
|#  <br/> |Digit placeholder. Displays either a digit or nothing. Leading and trailing zeros are not displayed. If more digits than placeholders are to the left of the decimal, all digits are displayed. If more digits than placeholders are to the right of the decimal, the fraction is rounded to the number of placeholders. For a dimension, if the placeholder is the leftmost digit, subunits that are 0 are not displayed. For example, FORMAT(0ft 11.25in,"#.##u") displays 11.25in. |
|0  <br/> |Digit placeholder (zero). Displays either a digit or nothing. Leading and trailing zeros are displayed. If more digits than placeholders are to the left of the decimal, all digits are displayed. If more digits than placeholders are to the right of the decimal, the fraction is rounded to the number of placeholders. For a dimension, subunits that are 0 are displayed. For example, FORMAT(2ft 11.33in,"0.## u") displays 2 ft. 11.33 in. |
|. |Decimal placeholder. Determines how many digits are displayed to the left and right of the decimal position. In a multipart unit, the decimal is used in the smallest (rightmost) subunit. Displays the decimal character defined for the system's **Region and Language** settings (Control Panel). For example, FORMAT(250 cm,"0.000 u") displays 250.000 cm. |
|,  <br/> |Thousands separator. If surrounded by digit placeholders (# or 0), the separator separates thousands from hundreds within a number that has four or more digits to the left of the decimal. Displays the thousands separator defined for the system's **Region and Language** settings (Control Panel). |
|E- E+ e- e+  <br/> |Scientific format. If the format contains at least one digit placeholder to the right of these symbols, the number is displayed in scientific format. Inserts the E or e between the number and its exponent. For E+ or e+, displays the plus (+) sign before positive exponents and the minus (-) sign before negative exponents. For E- or e-, displays the minus (-) sign only when the exponent is negative. For example, FORMAT(12345.67,"###.#e+#") displays 123.5e+2. |
|u or U  <br/> |Short label placeholder. Inserts abbreviated unit labels after each subunit. For example: in., ft., deg. The U placeholder inserts mixed-case labels, while the u placeholder inserts lowercase labels. Inserts the same number of spaces before the label as before the placeholder. For example, FORMAT(12 c 13 d,"#u") displays 13c1. |
|uu or UU  <br/> |Long label placeholder. Inserts unit labels after each subunit. For example: inches, feet, degrees The U placeholder inserts mixed-case labels, while the u placeholder inserts lowercase labels. Inserts the same number of spaces before the label as before the placeholder. For example, FORMAT(12.43in,"# #/4 UU") displays 12 2/4 INCHES. |
|uuu or UUU  <br/> |Universal label placeholder. Inserts the universal (internal to Visio) form of unit labels after each subunit. The U placeholder inserts mixed-case labels, while the u placeholder inserts lowercase labels. Inserts the same number of spaces before the label as before the placeholder. |
|/  <br/> |Fraction placeholder. Displays expression as a whole number with fraction if a leading digit placeholder is present. Otherwise, displays only the whole number in the numerator. If a number follows the digit placeholder in the denominator, rounds the fraction to the nearest fraction whose numerator is 1 and simplifies it. If a number is specified in the denominator without the digit placeholder, rounds to the nearest fraction but does not simplify it. For example, FORMAT(12.43,"# #/4") displays 12 2/4. |
|space  <br/> |Displays a space character in the formatted output. To display another character, use the backslash (\) character. |
   
## Currency values

|**Character**|**Description**|
|:-----|:-----|
|$  <br/> |Currency symbol. Displays the currency symbol defined for the system's **Region and Language** settings (Control Panel)  <br/> |
|u or U  <br/> |Short label placeholder. Inserts the standard symbol for local currency or the three-character currency abbreviations for nonlocal currencies. For example, $99.00, 42.70 FRF. The u placeholder inserts lowercase, and U inserts mixed-case labels. |
|uu or UU  <br/> |Long label placeholder. Inserts long currency labels after each subunit. For example: U.S. dollar, French franc. The u placeholder inserts lowercase, and U inserts mixed-case labels. |
|uuu or UUU  <br/> |Universal label placeholder. Inserts the universal, three-character currency abbreviations for all currencies after each subunit. For example, 99.00 USD, 42.70 FRF. The u placeholder inserts lowercase, and U inserts mixed-case labels. Inserts the same number of spaces before the label as before the placeholder. |
   
## Text values

|**Character**|**Description**|
|:-----|:-----|
|\  <br/> |Displays the next character as is. To display the backslash character, type \\. See also "text". |
|"text" or 'text'  <br/> |Displays the text enclosed in quotation marks as is. See also \ (backslash). |
|@  <br/> |Text placeholder. Replaces a string if the value of an expression is a string. For example, FORMAT("Hello", "'You entered ('@')'" ) results in "You entered (Hello)". |
|@+  <br/> |Uppercase text placeholder. For string values, substitutes the input with uppercase. For example, FORMAT("Hello", "@ @+ @-" ) results in "Hello HELLO hello)". |
|@-  <br/> |Text placeholder. For string values, substitutes the input with lowercase. For example, FORMAT("Hello", "@ @+ @-" ) results in "Hello HELLO hello)". |
   
## Date values

|**Character**|**Description**|
|:-----|:-----|
|c or C  <br/> |Date or time placeholder. Displays date and time values using a short (c) or long (C) date format, and the general time format. Visio versions 4.0 and earlier ignore this placeholder. For example: FORMAT(DATETIME("6/25/07 12:05"),"C") displays Monday, June 25, 2007 12:05:00 PM. FORMAT(DATETIME("Jun. 25, 2007"),"c") displays 6/25/2007. |
|/  <br/> |Date separator. If the expression is a date, separates the date components. Displays the date separator defined for the system's **Region and Language** settings (Control Panel). |
| [ ]  <br/> |Elapsed date placeholder. Used with the d, dd, w, and ww placeholders to display duration units. For example, [d] or [dd] is elapsed days and [w] or [ww] is elapsed weeks. |
|d  <br/> |Day placeholder. Displays the day as a number (1-31) without a leading zero. |
|dd  <br/> | Day placeholder. Displays the day as a number (01-31) with a leading zero. |
|ddd or w  <br/> |Short day of week placeholder. Displays the day as an abbreviation (Sun-Sat). |
|dddd or w  <br/> |Long day of week placeholder. Displays the day as a full name (Sunday-Saturday). |
|ddddd  <br/> |Short date placeholder. Displays a date in the short form defined for the system's **Region and Language** settings (Control Panel). |
|dddd  <br/> |Long date placeholder. Displays a date in the long form defined for the system's **Region and Language** settings (Control Panel). |
|D  <br/> |Day placeholder for Traditional Chinese. Displays the day of the month as the textual representation of the ordinal number. Locale-specific. |
|D_c  <br/> |Day placeholder for Traditional Chinese. Displays the day of the month as the textual representation of the ordinal number. Independent of the user locale. |
|w_c or w_c  <br/> |Day placeholder for Traditional Chinese. Independent of the user locale. |
|w_e  <br/> |Short day of week placeholder for English. Displays the day as an abbreviation (Sun-Sat). Independent of the user locale. |
|w_j  <br/> |Short day of week placeholder for Japanese. Displays the day as an abbreviation. Independent of the user locale. |
|w_k  <br/> |Short day of week placeholder for Korean. Displays the day as an abbreviation. Independent of the user locale. |
|w_s or w_s  <br/> |Day placeholder for Simplified Chinese. Independent of the user locale. |
|ww_e  <br/> |Long day of week placeholder for English. Displays the day as a full name (Sunday-Saturday). Independent of the user locale. |
|ww_j  <br/> |Long day of week placeholder for Japanese. Displays the day as a full name. Independent of the user locale. |
|w_k  <br/> |Long day of week placeholder for Korean. Displays the day as a full name. Independent of the user locale. |
|M  <br/> |Month placeholder. Displays the month as a number (1-12) without a leading zero. See also m (minute placeholder). |
|MM  <br/> |Month placeholder. Displays the month as a number (01-12) with a leading zero. See also mm (minute placeholder). |
|MMM  <br/> |Month placeholder. Displays the month in abbreviated form (Jan-Dec). |
|MMMM  <br/> |Month placeholder. Displays the full name of the month (January-December). |
|MMMM_c  <br/> |Month placeholder for Traditional Chinese. Displays the full name of the month. Independent of the user locale. |
|MMMM_e  <br/> |Month placeholder for English. Displays the full name of the month. Independent of the user locale. |
|yy  <br/> |Year placeholder. Displays the year as a two-digit number (00-99). |
|yyyy  <br/> |Year placeholder. Displays the year as a four-digit number (1900-2078). |
|g  <br/> |Year placeholder. Locale-specific. For Japanese, displays short version for Gengo era. For Korean, displays Korean year label followed by a space. |
|g_j  <br/> |Year placeholder. For Japanese, displays short version for Gengo era. Independent of user locale. |
|gg or G  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays short version for formal year label. For Japanese, displays short version for Gengo era in Kanji. For Korean, displays Korean year label followed by a space. |
|gg_c  <br/> |Year placeholder. For Traditional Chinese, displays short version for formal year label. Independent of user locale. |
|gg_j  <br/> |Year placeholder. For Japanese, displays short version for Gengo era in Kanji. Independent of user locale. |
|gg_k  <br/> |Year placeholder. For Korean, displays Korean year label followed by a space. Independent of user locale. |
|ggg or GG  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays full version for formal year label. For Japanese, displays full version for Gengo era in Kanji. For Korean, displays Korean year label followed by a space. |
|ggg_c  <br/> |Year placeholder. For Traditional Chinese, displays full version for formal year label. Independent of user locale. |
|ggg_j  <br/> |Year placeholder. For Japanese, displays full version for Gengo era in Kanji. Independent of user locale. |
|e  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays string representing the Julian year. For Japanese, displays Gengo year as one or two digits and no leading zero. For Korean, displays the Korean year as a four-digit Arabic numeral. |
|e_c  <br/> |Year placeholder. For Traditional Chinese, displays string representing the Julian year. Independent of user locale. |
|e_j  <br/> |Year placeholder. For Japanese, displays Gengo year as a one- or two-digit Arabic numeral. Independent of user locale. |
|e_k  <br/> |Year placeholder. For Korean, displays the Korean year as a four-digit Arabic numeral. Independent of user locale. |
|E  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays a string representing the republic year. For Japanese, displays Gengo year as one or two digits and no leading zero. For Korean, displays the Korean year as a four-digit Arabic numeral. |
|E_c  <br/> |Year placeholder. For Traditional Chinese, displays a string representing the republic year. Independent of user locale. |
|ee  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays string representing the Julian year. For Japanese, displays Gengo year as a two-digit Arabic numeral with leading zero if needed. For Korean, displays the Korean year as a four-digit Arabic numeral. |
|ee_j  <br/> |Year placeholder. For Japanese, displays Gengo year as a two-digit Arabic numeral. Independent of user locale. |
|EE  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays a string representing the republic year. For Japanese, displays Gengo year as a two-digit Arabic numeral with leading zero if needed. For Korean, displays the Korean year as a four-digit Arabic numeral. |
|n or N  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays the republic year as an Arabic numeral. For Japanese, displays Gengo year as one or two digits and no leading zero. For Korean, displays the Korean year as a four-digit Arabic numeral. |
|n_c  <br/> |Year placeholder. For Traditional Chinese, displays the republic year as an Arabic numeral. Independent of user locale. |
|nn or NN  <br/> |Year placeholder. Locale-specific. For Traditional Chinese, displays the republic year as an Arabic numeral. For Japanese, displays Gengo year as a two-digit Arabic numeral with leading zero if needed. For Korean, displays the Korean year as a four-digit Arabic numeral. |
   
## Time values

|**Character**|**Description**|
|:-----|:-----|
|:  <br/> |Time separator. Displays the time defined for the system's **Region and Language** settings (Control Panel). |
|[ ]  <br/> |Elapsed time placeholder. Used with the h, hh, m, mm, s, and ss placeholders to display duration units. For example, [h] or [hh] is elapsed hours, [m] or [mm] is elapsed minutes, and [s] or [ss] is elapsed seconds. |
|h  <br/> |Hour placeholder. Displays the hour without a leading zero in 12-hour form (0-12). |
|hh  <br/> |Hour placeholder. Displays the hour with a leading zero in 12-hour form (00-12). |
|H  <br/> |Hour placeholder. Displays the hour without a leading zero in 24-hour form (0-24). |
|HH  <br/> |Hour placeholder. Displays the hour with a leading zero in 24-hour form (00-24). |
|m  <br/> |Minute placeholder. Displays the minutes without a leading zero (0-59). |
|mm  <br/> |Minute placeholder. Displays the minutes with a leading zero (00-59). |
|s  <br/> |Second placeholder. Displays the seconds without a leading zero (0-59). |
|ss  <br/> |Second placeholder. Displays the seconds with a leading zero (00-59). |
|t  <br/> |AM/PM abbreviation. Displays the abbreviation defined for the system's **Region and Language** settings (Control Panel). |
|tt  <br/> |AM/PM designator. Displays the full designator defined for the system's **Region and Language** settings (Control Panel). |
|t_c or tt_c  <br/> |Traditional Chinese AM/PM designator. Displays the designator. Independent of user locale. |
|t_k or tt_k  <br/> |Korean AM/PM designator. Displays the designator. Independent of user locale. |
|t_j or tt_j  <br/> |Japanese AM/PM designator. Displays the designator. Independent of user locale. |
|t_e  <br/> |English AM/PM designator. Displays the short designator. Independent of user locale. |
|tt_e  <br/> |English AM/PM designator. Displays the full designator. Independent of user locale. |
|t_s or tt_s  <br/> |Simplified Chinese AM/PM designator. Displays the designator. Independent of user locale. |
|T  <br/> |General time format. |
   

