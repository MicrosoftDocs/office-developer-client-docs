---
title: "Default Cell (Hyperlinks Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251545
 
ms.localizationpriority: medium
ms.assetid: 0edea0ea-58dd-15da-6d4f-185d40133452

description: "Determines the default hyperlink for a shape or page. Set the value of this cell to TRUE to set a hyperlink as the default."
---

# Default Cell (Hyperlinks Section)

Determines the default hyperlink for a shape or page. Set the value of this cell to TRUE to set a hyperlink as the default.
  
## Remarks

You can also set the default hyperlink by selecting a shape, clicking **Hyperlink** on the **Insert** tab, selecting a hyperlink, and then clicking **Default**. The default hyperlink appears in bold text.
  
To get a reference to the Default cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Hyperlink. *Name*  .Default           where Hyperlink. *Name*  is the row name  <br/> |
   
To get a reference to the Default cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionHyperlink** <br/> |
|Row index:  <br/> |**visRow1stHyperlink** +  *i*           where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visHLinkDefault** <br/> |
   

