---
title: "SubAddress Cell (Hyperlinks Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm985
 
ms.localizationpriority: medium
ms.assetid: 949448fd-0f85-b56a-945e-1da0e48609e8
description: "Specifies a location within the target document to link to."
---

# SubAddress Cell (Hyperlinks Section)

Specifies a location within the target document to link to.
  
## Remarks

For example, if the Address cell is "Drawing1.vsdx", the SubAddress cell can specify a page name such as "Page-3". If the Address cell is the Microsoft Excel file "Samples.xlsx", the value of this cell can be a worksheet or range within a worksheet, such as "Worksheet Functions" or "Sheet1!A1:D10". If the Address cell is "https://www.microsoft.com/office/", the value of this cell can be a named anchor within the document, such as "solutions".
  
You can also set the value of this cell in the **Hyperlinks** dialog box (in the **Links** group on the **Insert** tab, click **Hyperlink**).
  
To get a reference to the SubAddress cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Hyperlink.  *name*  .SubAddress where Hyperlink  *.name*  is the row name  <br/> |
   
To get a reference to the **SubAddress** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionHyperlink** <br/> |
| **Row index:**  <br/> |**visRow1stHyperlink** +  *i*  where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visHLinkSubAddress** <br/> |
   

