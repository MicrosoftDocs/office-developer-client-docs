---
title: "LangID Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033769
 
ms.localizationpriority: medium
ms.assetid: c68289b8-ef45-9e1e-12ae-6613587e4990

description: "Indicates the language in which the text was entered."
---

# LangID Cell (Character Section)

Indicates the language in which the text was entered. 
  
## Remarks

For a list of languages supported by Microsoft Office applications, see the [DocLangID](doclangid-cell-document-properties-section.md) Cell (Document Properties Section) topic. 
  
To get a reference to the LangID cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Char.LangID[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the LangID cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionCharacter** <br/> |
| Row index:  <br/> |**visRowCharacter** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visCharacterLangID** <br/> |
   

