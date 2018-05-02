---
title: "LangID Cell (Annotation Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60048
 
localization_priority: Normal
ms.assetid: b6f5ea5e-b350-0817-d631-f059b9b95c23

description: "Indicates the language in which the comment was entered."
---

# LangID Cell (Annotation Section)

Indicates the language in which the comment was entered.
  
> [!NOTE]
> This cell is used for tracking comments only when opening a .vsd file in Microsoft Visio 2013 or when saving a .vsdx file in the .vsd file format. It is not used for tracking comments in .vsdx documents in Visio 2013. 
  
## Remarks

This value is the locale ID (LCID) of the language that is active on the language bar when the comment was entered. For a list of languages supported by Microsoft Office applications, see the [DocLangID](doclangid-cell-document-properties-section.md) Cell (Document Properties Section) topic. 
  
To get a reference to the LangID cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Annotation.LangID[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the LangID cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionAnnotation** <br/> |
| Row index:  <br/> |**visRowAnnotation** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visAnnotationLangID** <br/> |
   

