---
title: "Using Wildcard Characters in String Comparisons"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 37dda2b8-c710-4f73-bb2a-76a1348c42fe
description: "Built-in pattern matching provides a versatile tool for making string comparisons. The following table shows the wildcard characters you can use with the Like operator and the number of digits or strings they match."
---

# Using Wildcard Characters in String Comparisons

Built-in pattern matching provides a versatile tool for making string comparisons. The following table shows the wildcard characters you can use with the **Like** operator and the number of digits or strings they match. 
  
|**Character(s) in  *pattern***|**Matches in  *expression***|
|:-----|:-----|
|? or _ (underscore)  <br/> |Any single character  <br/> |
|\* or %  <br/> |Zero or more characters  <br/> |
|#  <br/> |Any single digit (0 - 9)  <br/> |
|[ *charlist*  ]  <br/> |Any single character in  *charlist*  <br/> |
|[! *charlist*  ]  <br/> |Any single character not in  *charlist*  <br/> |
   
You can use a group of one or more characters ( *charlist*  ) enclosed in brackets ([ ]) to match any single character in  *expression,*  and  *charlist*  can include almost any characters in the ANSI character set, including digits. You can use the special characters opening bracket ([ ), question mark (?), number sign (#), and asterisk (*) to match themselves directly only if enclosed in brackets. You cannot use the closing bracket ( ]) within a group to match itself, but you can use it outside a group as an individual character. 
  
In addition to a simple list of characters enclosed in brackets,  *charlist*  can specify a range of characters by using a hyphen (-) to separate the upper and lower bounds of the range. For example, using [A-Z] in  *pattern*  results in a match if the corresponding character position in  *expression*  contains any of the uppercase letters in the range A through Z. You can include multiple ranges within the brackets without delimiting the ranges. For example, [a-zA-Z0-9] matches any alphanumeric character. 
  
It is important to note that the ANSI SQL wildcards (%) and (_) are only available with Microsoft® Jet version 4.X and the Microsoft OLE DB Provider for Jet. They will be treated as literals if used through Microsoft Access or DAO.
  
Other important rules for pattern matching include the following:
  
- An exclamation mark (!) at the beginning of  *charlist*  means that a match is made if any character except those in  *charlist*  are found in  *expression*  . When used outside brackets, the exclamation mark matches itself. 
    
- You can use the hyphen (-) either at the beginning (after an exclamation mark if one is used) or at the end of  *charlist*  to match itself. In any other location, the hyphen identifies a range of ANSI characters. 
    
- When you specify a range of characters, the characters must appear in ascending sort order (A-Z or 0-100). [A-Z] is a valid pattern, but [Z-A] is not.
    
- The character sequence [ ] is ignored; it is considered to be a zero-length string ("").
    

