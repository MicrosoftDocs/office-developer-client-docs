---
title: "ClippingPath Cell (Foreign Image Info Section)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference 
ms.localizationpriority: medium
ms.assetid: 0ec70417-5b23-45af-95a0-1b26f6791699
description: "Contains a reference to the geometry of the path that an image is bounded by."
---

# ClippingPath Cell (Foreign Image Info Section)

Contains a reference to the geometry of the path that an image is bounded by.
  
## Remarks

If the **ClippingPath** cell points to a valid path, the image is clipped so that the image is rendered inside of the path. If the **ClippingPath** cell is empty or contains an invalid entry, then the image will be rendered with a rectangular clip, using the scale and offset values.
  
> [!NOTE]
> Only paths defined by a [Geometry](geometry-section.md) section in the image's ShapeSheet are valid entries for the **ClippingPath** cell. Cross-sheet references cannot be used to define an image clipping path.
  
To get a reference to the **ClippingPath** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use:
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ClippingPath  <br/> |

To get a reference to the **ClippingPath** cell by index from a program, use the **CellsSRC** property with the following arguments:
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowForeign** <br/> |
| **Cell index:**  <br/> |**visFrgnImgClippingPath** <br/> |

## Example

You can change the bounding shape of an image to an oval by doing the following:
  
- Insert the picture onto the drawing canvas.

- Right-click the picture and then select **Show ShapeSheet**.

- Right-click anywhere in the ShapeSheet and select **Insert Section**.

- In the **Insert Section** dialog box, select **Geometry** and then click **OK**.

- In the new Geometry section (e.g. "Geometry2"), delete all but one row.

- Right-click the remaining row and then click **Change Row Type**.

- In the **Change Row Type** dialog box, select **Ellipse** and then click **OK**.

- In the **Foreign Image** section, set the formula for the **ClippingPath** cell to `="Geometry2.Path"` and then accept the formula.
