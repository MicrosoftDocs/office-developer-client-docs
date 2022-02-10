---
title: "Calendar Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60027
 
ms.localizationpriority: medium
ms.assetid: f5dcc6d9-474a-9ecb-21f5-56415d934890

description: "Determines the calendar that is used for shape data when the data type is Date."
---

# Calendar Cell (Shape Data Section)

Determines the calendar that is used for shape data when the data type is Date.
  
## Remarks

The possible values are: 0 (Western), 1 (Arabic Hijri), 2 (Hebrew Lunar), 3 (Taiwan Calendar), 4 (Japanese Emperor Reign), 5 (Thai Buddhist), 6 (Korean Danki), 7 (Saka Era), 8 (English transliterated), and 9 (French transliterated ). 
  
To get a reference to the Calendar cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Prop.  *name*  .Calendar            where Prop.  *name*  is the row name  <br/> |
   
To get a reference to the Calendar cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionProp** <br/> |
| Row index:  <br/> |**visRowProp** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visCustPropsCalendar** <br/> |
   

