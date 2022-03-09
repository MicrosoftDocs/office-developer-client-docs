---
title: "Description Cell (Hyperlinks Section)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm230
 
ms.localizationpriority: medium
ms.assetid: 2f571c65-6b7a-5a3a-c075-3c52d3ab989b
description: "Represents a descriptive text string for a hyperlink."
---

# Description Cell (Hyperlinks Section)

Represents a descriptive text string for a hyperlink.
  
## Remarks

Use this cell to store comments about the hyperlink; for example, "Link to our pricing website."
  
You can also set the value of this cell in the **Hyperlinks** dialog box (click **Hyperlink** on the **Insert** tab).
  
To get a reference to the Description cell by name from another formula, or from a program using the **CellsU** property, use:
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Hyperlink. *Name* .Description where Hyperlink. *Name* is the name of the hyperlink row.  <br/> |

To get a reference to the Description cell by index from a program, use the **CellsSRC** property with the following arguments:
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionHyperlink** <br/> |
| **Row index:**  <br/> |**visRow1stHyperlink** + *i*           <br/>where *i* = 0, 1, 2... |
| **Cell index:**  <br/> |**visHLinkDescription** <br/> |
