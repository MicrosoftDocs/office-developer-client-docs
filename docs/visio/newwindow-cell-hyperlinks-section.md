---
title: "NewWindow Cell (Hyperlinks Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm695
 
localization_priority: Normal
ms.assetid: 44995137-d241-937a-c097-0f9d79203cdf

description: "Specifies whether to open the hyperlink in a new window."
---

# NewWindow Cell (Hyperlinks Section)

Specifies whether to open the hyperlink in a new window.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Open the linked page, document, or website in a new window.  <br/> |
| FALSE  <br/> | Default. Do not open a new window for the hyperlink.  <br/> |
   
## Remarks

To get a reference to the NewWindow cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Hyperlink.  *Name*  .NewWindow            where Hyperlink.  *Name*  is the row name  <br/> |
   
To get a reference to the NewWindow cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionHyperlink** <br/> |
| Row index:  <br/> |**visRow1stHyperlink** +  *i*            where  *i*  = 0, 1, 2, ...  <br/> |
| Cell index:  <br/> |**visHLinkNewWin** <br/> |
   

