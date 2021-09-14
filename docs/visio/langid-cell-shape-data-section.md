---
title: "LangID Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033771
 
ms.localizationpriority: medium
ms.assetid: 6bd2781a-d4e7-136f-8996-62ebc5f890ab

description: "Indicates the language in which the shape data value was entered."
---

# LangID Cell (Shape Data Section)

Indicates the language in which the shape data value was entered. 
  
## Remarks

For a list of languages supported by Microsoft Office System applications, see the [DocLangID](doclangid-cell-document-properties-section.md) Cell (Document Properties Section). 
  
To get a reference to the LangID cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Prop.  *name*  .LangID            where Prop.  *name*  is the row name  <br/> |
   
To get a reference to the LangID cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionProp** <br/> |
| Row index:  <br/> |**visRowProp** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCustPropsLangID** <br/> |
   

