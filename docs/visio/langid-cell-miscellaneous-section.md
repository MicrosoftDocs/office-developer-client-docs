---
title: "LangID Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60051
 
ms.localizationpriority: medium
ms.assetid: 815e0df8-5ebf-ef1b-d620-bce8abb69f1a
description: "Indicates the language in which cell formulas were created."
---

# LangID Cell (Miscellaneous Section)

Indicates the language in which cell formulas were created. 
  
## Remarks

For a list of languages supported by Microsoft Office applications, see the [DocLangID](doclangid-cell-document-properties-section.md) Cell (Document Properties Section) topic. 
  
To get a reference to the LangID cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LangID  <br/> |
   
To get a reference to the LangID cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowMisc** <br/> |
| Cell index:  <br/> |**visObjLangID** <br/> |
   

