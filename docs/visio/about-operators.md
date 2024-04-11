---
title: "About Operators"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251824
 
ms.localizationpriority: medium
ms.assetid: 43128ea2-c0d9-c45f-31e6-768a80ae59b2
description: "You can use operators in formulas to perform arithmetic operations (addition, subtraction, multiplication, and so on) or logical comparisons (greater than, less than, equal to, and so on). You also can control the order of evaluation in a formula by enclosing expressions in parentheses. Use the ampersand operator to combine (concatenate) character strings."
---

# About Operators

You can use operators in formulas to perform arithmetic operations (addition, subtraction, multiplication, and so on) or logical comparisons (greater than, less than, equal to, and so on). You also can control the order of evaluation in a formula by enclosing expressions in parentheses. Use the ampersand operator to combine (concatenate) character strings.
  
Microsoft Visio automatically attempts to convert data types when an operation or function requires a specific type of data. For example, the multiplication operator requires numeric arguments, and the ampersand (string concatenation) operator requires string arguments. If the argument cannot be converted to the required data type, a default value is provided. The default value is the typed equivalent of nothing: zero for numbers, FALSE for Boolean values, "" for strings, and so on.
  
The following table shows examples of expressions and their results.
  
|**Expression**|**Result**|**Description**|
|:-----|:-----|:-----|
| 2 \* 5 &amp; " cents"  <br/> | "10 cents"  <br/> | The &amp; operator (string concatenation) requires string arguments, so the numeric result of 2 \* 5 is automatically converted to the string "10". |
| 5 \* "2"  <br/> | 10  <br/> | The \* operator (multiplication) requires numeric arguments, so the string "2" is automatically converted to the equivalent number 2. |
| 5 \* "sheep"  <br/> | 0  <br/> | The \* operator (multiplication) requires numeric arguments, so because the string "sheep" cannot be converted to a number, zero is used as its numeric equivalent. |
   
## Arithmetic operators

Arithmetic operators perform operations on numbers. The plus (+) and minus (-) operators can be used alone as unary operators to establish the sign of a number. The percent (%) operator is also a unary operator and identifies the number as a percentage.
  
|**Operator**|**Action**|**Example**|**Result**|
|:-----|:-----|:-----|:-----|
| +  <br/> | Unary plus  <br/> | +37  <br/> | 37  <br/> |
| -  <br/> | Unary minus  <br/> | -37  <br/> | -37  <br/> |
| %  <br/> | Unary percentage  <br/> | 37%  <br/> | .37  <br/> |
| ^  <br/> | Exponentiation  <br/> | 5 ^ 2  <br/> | 25  <br/> |
| \*  <br/> | Multiplication  <br/> | 5 \* 2  <br/> | 10  <br/> |
| /  <br/> | Division  <br/> | 5 / 2  <br/> | 2.5  <br/> |
| +  <br/> | Addition  <br/> | 5 + 2  <br/> | 7  <br/> |
| -  <br/> | Subtraction  <br/> | 5 - 2  <br/> | 3  <br/> |
   
## Comparison operators

Comparison operators are used to construct logical expressions. A logical expression evaluates to either TRUE or FALSE.
  
|**Operator**|**Alternative**|**Action**|**Example**|**Result**|
|:-----|:-----|:-----|:-----|:-----|
| \>  <br/> | _GT_  <br/> | Greater than  <br/> | 5 \> 2  <br/> | TRUE  <br/> |
| \<  <br/> | _LT_  <br/> | Less than  <br/> | 5 \< 2  <br/> | FALSE  <br/> |
| \>=  <br/> | _GE_  <br/> | Greater than or equal to  <br/> | 5 \>= 2  <br/> | TRUE  <br/> |
| \<=  <br/> | _LE_  <br/> | Less than or equal to  <br/> | 5 \<= 2  <br/> | FALSE  <br/> |
| =  <br/> | _EQ_  <br/> | Equal to  <br/> | 5 = 2  <br/> | FALSE  <br/> |
| \<\>  <br/> | _NE_  <br/> | Not equal to  <br/> | 5 \<\> 2  <br/> | TRUE  <br/> |
   
The symbolic comparison operators (\>, \<, and so forth) are the best choice for most comparisons. The alternative operators (_GT_, _LT_, and so forth) perform an exact comparison to the full 15 digits of precision that Visio uses to store values internally.
  
When you compare rounded or calculated values by using the alternative operators, FALSE might be returned, when for all practical purposes the expression should evaluate to TRUE.
  
When you use comparison operators to compare text strings, the strings are first converted into numeric values. Text strings that cannot be converted return a value of 0; therefore, comparisons vary and might not produce the results you expect. To do a standard string comparison, use the function STRSAME or STRSAMEEX.
  
## Order of evaluation

When a formula contains more than one expression, the expressions are evaluated in order according to the operation being performed. This table shows the order of evaluation of operators in Visio.
  
|**Order**|**Action**|**Operator**|
|:-----|:-----|:-----|
|First  <br/> |Positive  <br/> |+ (unary)  <br/> |
||Negative  <br/> |- (unary)  <br/> |
||Percent  <br/> |% (unary)  <br/> |
|Second  <br/> |Exponentiation  <br/> |^  <br/> |
|Third  <br/> |Multiplication  <br/> |\*  <br/> |
||Division  <br/> |/  <br/> |
|Fourth  <br/> |Addition  <br/> |+  <br/> |
||Subtraction  <br/> |-  <br/> |
|Fifth  <br/> |String concatenation  <br/> |&amp;  <br/> |
|Sixth  <br/> |Greater than  <br/> |\> or GT  <br/> |
||Greater than or equal to  <br/> |\>= or GE  <br/> |
||Less than  <br/> |\< or LT  <br/> |
||Less than or equal to  <br/> |\<= or LE  <br/> |
|Seventh  <br/> |Equal  <br/> |= or EQ  <br/> |
||Not equal  <br/> |\<\> or NE  <br/> |
   
You can change the order of evaluation by enclosing expressions in parentheses. Visio evaluates expressions within parentheses first, from left to right. For example:
  
4 + 5 \* 6 = 4 + 30 = 34
  
(4 + 5) \* 6 = 9 \* 6 = 54
  
If expressions in parentheses are nested, the expression in the innermost set of parentheses is evaluated first.
  
## Ampersand operator

The ampersand operator returns a new character string. You can create compound words and phrases using the ampersand operator. Use the following syntax:
  
"string1" &amp; "string2"
  
 **Example**
  
"dog" &amp; "house" returns "doghouse"
  

