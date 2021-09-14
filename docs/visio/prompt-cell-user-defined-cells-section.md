---
title: "Prompt Cell (User-Defined Cells Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm840
 
ms.localizationpriority: medium
ms.assetid: d0f91e7d-2373-cfef-e105-fb17e77c7f2d

description: "Specifies a descriptive prompt or comment for the user-defined cell. The application automatically encloses the prompt text in quotation marks () to indicate that it is a text string. If you type an equal sign (=) and omit the quotation marks, you can enter a formula in this cell that the application evaluates."
---

# Prompt Cell (User-Defined Cells Section)

Specifies a descriptive prompt or comment for the user-defined cell. The application automatically encloses the prompt text in quotation marks (" ") to indicate that it is a text string. If you type an equal sign (=) and omit the quotation marks, you can enter a formula in this cell that the application evaluates.
  
## Remarks

To get a reference to the Prompt cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | User.  *Name*  .Prompt            where User.  *Name*  is the row name  <br/> |
   
To get a reference to the Prompt cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionUser** <br/> |
| Row index:  <br/> |**visRowUser +** *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visUserPrompt** <br/> |
   

