---
title: "About Strings"
ms.author: null
author: null
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251826
ms.prod: null
localization_priority: Normal
ms.assetid: e1174d8f-70cb-4595-7906-889da15367db
description: "Formulas can contain strings. To format string output, such as in a prompt cell, a shape data item value, or a text field, you specify a format picture. Output can be formatted as a number-unit pair, string, date-time, duration, or currency. For example, the format picture0 #/10 uuformats the number-unit pair 10.9cm as10 9/10 centimeters."
---

# About Strings

Formulas can contain strings. To format string output, such as in a prompt cell, a shape data item value, or a text field, you specify a format picture. Output can be formatted as a number-unit pair, string, date-time, duration, or currency. For example, the format picture "0 #/10 uu" formats the number-unit pair 10.9cm as "10 9/10 centimeters".
  
You can use format pictures in the **Format** cell of the Shape Data section and as an argument to the **FORMAT** or **FORMATEX** function. When you insert a text field, format pictures appear in the list of formats in the **Field** dialog box ( **Insert** tab). 
  
## Using functions to format strings

In any formula that resolves to a string, including custom text field formulas, you can use the **FORMAT** or **FORMATEX** function. The FORMAT function returns a string of the formatted output. The **FORMATEX** function converts untyped input to the units you choose for the formatted result. 
  
## Displaying formatted shape data

You can format the displayed value of a shape data item by entering a format picture in the Format cell.
  
For example, a project timeline shape can have a shape data item that measures the cost of a process. By default, a shape data item value is a string. To format the string "1200", you can enter "$###,###.00" in the Format cell so that the user sees a currency.
  
Microsoft Visio uses the settings on the **Currency** tab in the **Customize Format** dialog box in the **Region and Language** item in Control Panel to determine the currency symbol and thousands separator to display. (In **Control Panel**, click **Region and Language**, and then click **Additional Settings**.)
  
To convert a string to a currency value so that you can perform calculations with the value, use the CY function.
  
## Using functions to manipulate text strings

You can use functions to manipulate text strings, for example, to locate or replace certain characters in a text string. You can also get information about the position of a character in a string, or identify beginning and ending characters in a text string. 
  

