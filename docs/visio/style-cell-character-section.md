---
title: "Style Cell (Character Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251249
 
localization_priority: Normal
ms.assetid: 4372f1e1-f0a9-2f63-ff79-58f2afdceed5

description: "Shows the character formatting applied to a range of text in the shape's text block."
---

# Style Cell (Character Section)

Shows the character formatting applied to a range of text in the shape's text block.
  
|**Style**|**Value**|**Automation constant**|
|:-----|:-----|:-----|
| Bold  <br/> | &amp;H1  <br/> |**visBold** <br/> |
| Italic  <br/> | &amp;H2  <br/> |**visItalic** <br/> |
| Underline  <br/> | &amp;H4  <br/> |**visUnderLine** <br/> |
| Small caps  <br/> | &amp;H8  <br/> |**visSmallCaps** <br/> |
   
## Remarks

The Style cell contains formatting information applied to a sub-range of a shape's text if the Characters section contains multiple rows. Otherwise, it contains formatting information for all of the shape's text.
  
The value represents a binary number in which each bit indicates a character style. For example, a value of 3 represents text formatted in both italic and bold. If the value of Style is 0, the text is plain, or unformatted. You can test for a particular format using Boolean BIT\* functions. See your programming documentation for details about these functions.
  
To get a reference to the Style cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Char.Style[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Style cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionCharacter** <br/> |
| Row index:  <br/> |**visRowCharacter** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCharacterStyle** <br/> |
   
 *Example* 
  
Suppose the Color cell in the first row of a shape's Character section is set to this formula:
  
= IF(BITAND(Char.Style,1)=1,4,3)
  
Then if the first character of the shape's text is bold, the text covered by the first Character properties row will be blue (4); otherwise it will be green (3). This example assumes default colors are in effect.
  
The following is an example of setting the Style cell in a program. The first statement references the Style cell by name, and the second statement references the Style cell by index. Both statements apply italic to the text covered by the second row of a shape's Character section.
  

