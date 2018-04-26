---
title: "LIKE (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: decdd8fc-2184-4d97-b918-3ef6ab1ab40b
description: "Determines whether a specific character string matches a specified pattern. A pattern can include regular characters and wildcard characters. During pattern matching, regular characters must exactly match the characters specified in the character string. However, wildcard characters can be matched with arbitrary fragments of the character string. Using wildcard characters makes the LIKE operator more flexible than using the = and != string comparison operators."
---

# LIKE (Access custom web app)

Determines whether a specific character string matches a specified pattern. A pattern can include regular characters and wildcard characters. During pattern matching, regular characters must exactly match the characters specified in the character string. However, wildcard characters can be matched with arbitrary fragments of the character string. Using wildcard characters makes the **LIKE** operator more flexible than using the = and != string comparison operators. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 *Expression*  [ NOT ] **LIKE** *Pattern*  [ ESCAPE  *EscapeChar*  ] 
  
The **LIKE** operator contains the following arguments 
  
|**Argument name**|**Required**|**Description**|
|:-----|:-----|:-----|
| *Expression*  <br/> |Yes  <br/> |A valid expression.  <br/> |
| *Pattern*  <br/> |Yes  <br/> |The specific string of characters to search for in  *Expression*  . Can include wildcard characters. Refer to the Remarks for a list of valid wildcard characters.  <br/> |
| *EscapeChar*  <br/> |No  <br/> |A character that is put in front of a wildcard character to indicate that the wildcard should be interpreted as a regular character and not as a wildcard.  *EscapeChar*  is a character expression that has no default and must evaluate to only one character.  <br/> |
   
## Remarks

The following table contains the wildcard characters that are valid for use in the  *Pattern*  argument. 
  
|**Wildcard character**|**Description**|**Example**|
|:-----|:-----|:-----|
|%  <br/> |Any string of zero or more characters.  <br/> | *WHERE title LIKE '%computer%'*  finds all book titles with the word 'computer' anywhere in the book title.  <br/> |
|_ (underscore)  <br/> |Any single character.  <br/> | *WHERE au_fname LIKE '_ean'*  finds all four-letter first names that end with ean (Dean, Sean, and so on).  <br/> |
|[]  <br/> |Any single character within the specified range ([a-f]) or set ([abcdef]).  <br/> | *WHERE au_lname LIKE '[C-P]arsen'*  finds author last names ending with arsen and starting with any single character between C and P, for example Carsen, Larsen, Karsen, and so on.  <br/> |
|[^]  <br/> |Any single character not within the specified range ([^a-f]) or set ([^abcdef]).  <br/> | *WHERE au_lname LIKE 'de[^l]%'*  all author last names starting with de and where the following letter is not l.  <br/> |
   
When you perform string comparisons by using **LIKE**, all characters in the pattern string are significant. This includes leading or trailing spaces. If a comparison in a query is to return all rows with a string **LIKE** 'abc ' (abc followed by a single space), a row in which the value of that column is abc (abc without a space) is not returned. However, trailing blanks, in the expression to which the pattern is matched, are ignored. If a comparison in a query is to return all rows with the string **LIKE** 'abc' (abc without a space), all rows that start with abc and have zero or more trailing blanks are returned. 
  
If any one of the arguments is not of a string data type, it is converted to a string data type, if it is possible.
  

