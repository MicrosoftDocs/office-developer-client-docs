---
title: "Scratch Section" 
description: "Describes remarks for the Scratch Section, which is a work area for entering and testing formulas that can be referred to by other cells."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm2125
ms.localizationpriority: medium
ms.assetid: 144dd06f-7225-57db-fd19-a58d6bccf0e1
---

# Scratch Section

A work area for entering and testing formulas that can be referred to by other cells.
  
## Remarks

You can add this section by using the **Insert Section** dialog box. Right-click in the ShapeSheet window, and then click **Insert Section**.
  
The **Scratch** section is typically used to isolate repeated complex calculations. If your solution has a well-defined purpose, it's wiser to use a cell in the **User-Defined Cells** section for clarity because User cells can be named.
  
Cells in the **Scratch** section use units in two different ways. X and Y cells use drawing units; A through D cells don't use units. (In C programmers' jargon, X and Y cells are "typed," and cells A through D are "void.") The **Scratch X** and **Scratch Y** cells are often used for deriving *x-* and *y-* coordinates, such as **PinX** and **PinY**, or the X and Y cells found in a **Geometry** section cell. Scratch cells A through D can display whatever units you specify.
  
A further difference is the way these cells store point values. A point in Visio is a single data package for an ( *x,y*) coordinate. When a formula returns a point value, that value is interpreted in one of three ways, depending on the ShapeSheet cell the formula is in. Cells that relate to *x* -coordinates (for example, **PinX**, or cells in the X column of a **Geometry** section) extract just the *x* -coordinate part of a point value. Cells that relate to *y* -coordinates extract just the *y* -coordinate part of a point value.
  
For example, Visio extracts the formula `PNT(3,4)` in these three ways.
  
|**Cell**|**If you enter**|**Visio treats it as**|**Result**|
|:-----|:-----|:-----|:-----|
| X  <br/> | `PNT(3,4)` <br/> | `PNTX(PNT(3,4))` <br/> | 3.0000 in. |
| Y  <br/> | `PNT(3,4)` <br/> | `PNTY(PNT(3,4))` <br/> | 4.0000 in. |
| A-D  <br/> | `PNT(3,4)` <br/> | `PNT(3,4)` <br/> | PNT(3.0000 in., 4.0000 in.)  <br/> |
