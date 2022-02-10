---
title: "UIVisibility Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60090
 
ms.localizationpriority: medium
ms.assetid: df7f79df-770a-4868-e7e2-05c3828e23eb
description: "Determines whether the page name is exposed in the user interface (UI)."
---

# UIVisibility Cell (Page Properties Section)

Determines whether the page name is exposed in the user interface (UI).
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Display the page name in the UI (the default). |**visUIVNormal** <br/> |
|1  <br/> |Do not display the page name in the UI. |**visUIVHidden** <br/> |
   
## Remarks

Setting the UIVisibility cell to **visUIVHidden** prevents the page from appearing anywhere in the UI where the string containing the page name appears. For example, the page would not be listed as an option in the **Drawing Explorer** or on the page tabs. The page remains accessible, however, if you use Automation or UI paths that do not include the page name, for example, the **Print** command. 
  
 This cell is intended for use with document pages; it is not intended for use with markup overlay pages, which have the UIVisibility cell set to **visUIVHidden** by default and should not be changed. 
  
> [!NOTE]
> To hide a page from the document's **Print** command, make it a background page (**Type** property is **visTypeBackground** ) that is not used as a background by any page (shapes on background pages are printed when a page using it as a background is printed). The document's **Print** command only works with indexed pages, and background pages are not indexed. 
  
To get a reference to the UIVisibility cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |UIVisibility  <br/> |
   
To get a reference to the UIVisibility cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPage** <br/> |
|Cell index:  <br/> |**visPageUIVisibility** <br/> |
   

