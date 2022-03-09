---
title: "ShdwScaleFactor Cell (Page Properties Section)" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60083
 
ms.localizationpriority: medium
ms.assetid: 10979706-6dfe-5241-e862-3f94716d14fa
description: "Specifies the percentage to enlarge or reduce a shape's shadow."
---

# ShdwScaleFactor Cell (Page Properties Section)

Specifies the percentage to enlarge or reduce a shape's shadow.
  
## Remarks

Each shadow has a shadowed pin location, which is a point on the shadow that corresponds to the shape's pin. For example, if a shape's pin is in the center of the shape, then the shadowed pin location would be the point in the center of the shadow. When applying scale to simple shadows, magnification is centered at the shadowed pin location; when applying scale to oblique shadows, magnification is applied in the oblique direction.
  
This percentage is used when the shadow type for a shape is set to Page Default (ShapeShdwType cell equals **visFSTPageDefault** ).
  
To set this behavior for an individual shape, use the ShapeShdwScaleFactor cell in the Fill Format section.
  
This value corresponds to the value in the **Magnification** box on the **Shadows** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow).
  
To get a reference to the ShdwScaleFactor cell by name from another formula, or from a program using the **CellsU** property, use:
  
|**Value**|**Description**|
|:-----|:-----|
| Cell name:  <br/> | ShdwScaleFactor  <br/> |

To get a reference to the ShdwScaleFactor cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|**Value**|**Description**|
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageShdwScaleFactor** <br/> |
