---
title: "Calendar Cell (Text Fields Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60029
 
localization_priority: Normal
ms.assetid: 0c3e275e-25f0-3681-03f4-257145c19690

description: "Determines the calendar that is used for a text field when the data type is Date."
---

# Calendar Cell (Text Fields Section)

Determines the calendar that is used for a text field when the data type is Date.
  
## Remarks

The possible values are: 0 (Western), 1 (Arabic Hijri), 2 (Hebrew Lunar), 3 (Taiwan Calendar), 4 (Japanese Emperor Reign), 5 (Thai Buddhist), 6 (Korean Danki), 7 (Saka Era), 8 (English transliterated), and 9 (French transliterated ). 
  
To get a reference to the Calendar cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Fields.Calendar[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Calendar cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionTextField** <br/> |
| Row index:  <br/> |**visRowField** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visFieldCalendar** <br/> |
   

