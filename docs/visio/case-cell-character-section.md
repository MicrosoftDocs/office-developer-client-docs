---
title: "Case Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251250
 
ms.localizationpriority: medium
ms.assetid: cf063c05-5789-e037-700b-1e70df00e254

description: "Determines the case of a shape's text. All capital (uppercase) letters (1) and initial capital letters (2) do not change the appearance of text that was entered in all capital letters. The text must be entered in lowercase letters for these options to show an effect."
---

# Case Cell (Character Section)

Determines the case of a shape's text. All capital (uppercase) letters (1) and initial capital letters (2) do not change the appearance of text that was entered in all capital letters. The text must be entered in lowercase letters for these options to show an effect.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Normal case  <br/> |**visCaseNormal** <br/> |
| 1  <br/> | All capital (uppercase) letters  <br/> |**visCaseAllCaps** <br/> |
| 2  <br/> | Initial capital letters only  <br/> |**visCaseInitialCaps** <br/> |
   
## Remarks

To get a reference to the Case cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Char.Case[  *i*  ]            where  *i*  = <1>, 2, 3, ... |
   
To get a reference to the Case cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionCharacter** <br/> |
| Row index:  <br/> |**visRowCharacter** +  *i*            where  *i*  = 0, 1, 2, ... |
| Cell index:  <br/> |**visCharacterCase** <br/> |
   

