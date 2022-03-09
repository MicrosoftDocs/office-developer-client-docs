---
title: "Address Cell (Hyperlinks Section)" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251387
 
ms.localizationpriority: medium
ms.assetid: 3864aadd-3f86-c20e-1a74-b0aaff5106f7
description: "Specifies a URL address, file name, or UNC path to which to jump."
---

# Address Cell (Hyperlinks Section)

Specifies a URL address, file name, or UNC path to which to jump.
  
You can specify Address as a relative path based on the base path defined for the document in the **Hyperlink base** box on the **Summary** tab of the **Properties** dialog box (click the **File** tab, click **Info**, click **Properties**, and then click **Advanced Properties**). If the document has no base path, the application navigates based on the document path. If the document has not been saved, the hyperlink is undefined.
  
## Remarks

You can also set the value of the Address cell in the **Hyperlinks** dialog box (click **Hyperlink** on the **Insert** tab).
  
To get a reference to the Address cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|**Value**|**Description**|
|:-----|:-----|
|Cell name:  <br/> |Hyperlink. *name*  .Address  where Hyperlink. *name* is the name of the hyperlink row  <br/> |

To get a reference to the Address cell by name from another formula, or from a program, by using the **CellsU** property, use:
  
|**Value**|**Description**|
|:-----|:-----|
| Section index:  <br/> |**visSectionHyperlink** <br/> |
| Row index:  <br/> |**visRow1stHyperlink** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visHLinkAddress** <br/> |
