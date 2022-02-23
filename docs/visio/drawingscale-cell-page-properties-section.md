---
title: "DrawingScale Cell (Page Properties Section)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm265
 
ms.localizationpriority: medium
ms.assetid: bc447f22-a188-2c61-e33c-df0d401a4725
description: "Represents the value of the drawing unit in the current drawing scale. The drawing scale for the page is the ratio of the page unit shown in the PageScale cell to the drawing unit shown in the DrawingScale cell."
---

# DrawingScale Cell (Page Properties Section)

Represents the value of the drawing unit in the current drawing scale. The drawing scale for the page is the ratio of the page unit shown in the PageScale cell to the drawing unit shown in the DrawingScale cell.
  
You can set the DrawingScale cell to change the units of a page's rulers from a program. Here is an example of changing the measurement units from inches to centimeters from a program. In this case, we use the **ConvertResult** method to keep the distance the same but express it in different units.
  
```vb
Public Sub SetActivePageMeasurementToCM() 
Dim dsCell As Visio.Cell 
Set dsCell = ActivePage.PageSheet.Cells("DrawingScale") 
 dsCell.Result(visCentimeters) = _ 
 Application.ConvertResult _ 
 (dsCell.ResultIU,visInches,visCentimeters) 
End Sub 
```

You can determine the measurement system in a drawing by examining the **Units** property of the DrawingScale cell. After running the above macro the following statement executed in the Visual Basic Editor Immediate window will return *True*.
  
```vb
debug.print ActivePage.PageSheet.Cells("DrawingScale").Units = _ 
 visCentimeters 
```

## Remarks

This cell corresponds to the settings in the **Page Setup** dialog box (click the **Page Setup** arrow on the **Home** tab).
  
The units of the formula in the DrawingScale cell determine the measurement units used by the rulers in the drawing window. If you do not want to also change the drawing's scale, you can do one of the following:
  
- Keep the distance expressed in the DrawingScale cell the same but express it in different units.

- Change the distance expressed in the PageScale cell by the same factor that you change DrawingScale.

To get a reference to the DrawingScale cell by name from another formula, or from a program using the **CellsU** property, use:
  
|||
|:-----|:-----|
|Cell name:  <br/> |DrawingScale  <br/> |

To get a reference to the DrawingScale cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPage** <br/> |
|Cell index:  <br/> |**visPageDrawingScale** <br/> |
