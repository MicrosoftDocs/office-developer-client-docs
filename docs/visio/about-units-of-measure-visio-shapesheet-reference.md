---
title: "About Units of Measure (Visio ShapeSheet Reference)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251828
 
ms.localizationpriority: medium
ms.assetid: 48f765a8-7485-03c0-3484-d4ec07822600
description: "When you insert fields into text or build formulas, you often specify units of measure for the values you type."
---

# About Units of Measure (Visio ShapeSheet Reference)

When you insert fields into text or build formulas, you often specify units of measure for the values you type.
  
Microsoft Visio evaluates the result of a formula differently depending on the cell in which you enter the formula. In general, cells that represent shape position, a dimension, or an angle require a number-unit pair that consists of a number and the qualifying units needed to interpret the number. Many other cells don't require units and evaluate to a string, to TRUE or FALSE, or to an index. For example, the same formula that in the **FillForegnd** cell means color 5 from the drawing's color palette means TRUE (and locks the shape's width) in the LockWidth cell. 
  
Always specify a unit of measure when you enter a formula in a cell that expects a dimensional value. If you don't specify a unit of measure, Visio uses the default unit for that cell, which can be page units, drawing units, type units, duration units, or angular units.
  
## Units of measure

When indicating units of measure in ShapeSheet formulas, use the abbreviations listed in the following table.
  
|**To specify these units of measure**|**Use**|**Automation constant**|
|:-----|:-----|:-----|
| Centimeters  <br/> | cm  <br/> |**visCentimeters (69)** <br/> |
| Ciceros  <br/> | c  <br/> |**visCiceros (54)** <br/> |
| Date or time  <br/> | date  <br/> |**visDate (40)** <br/> |
| Degrees  <br/> | deg  <br/> |**visDegrees (81)** <br/> |
| Didots  <br/> | d  <br/> |**visDidots (53)** <br/> |
| Elapsed weeks  <br/> | ew  <br/> |**visElapsedWeek (43)** <br/> |
| Elapsed days  <br/> | ed  <br/> |**visElapsedDay (44)** <br/> |
| Elapsed hours  <br/> | eh  <br/> |**visElapsedHour (45)** <br/> |
| Elapsed minutes  <br/> | em  <br/> |**visElapsedMin (46)** <br/> |
| Elapsed seconds  <br/> | es  <br/> |**visElapsedSec (47)** <br/> |
| Feet  <br/> | ft  <br/> |**visFeet (66)** <br/> |
| Inches  <br/> | in  <br/> |**visInches (65)** <br/> |
| Kilometers  <br/> | km  <br/> |**visKilometers (72)** <br/> |
| Meters  <br/> | m  <br/> |**visMeters (71)** <br/> |
| Miles  <br/> | mi  <br/> |**visMiles (68)** <br/> |
| Millimeters  <br/> | mm  <br/> |**visMillimeters (70)** <br/> |
| Minutes  <br/> | '  <br/> |**visMin (84)** <br/> |
| Nautical miles  <br/> | nm  <br/> |**visNautMiles (76)** <br/> |
| Percent  <br/> | %  <br/> |**visPercent (33)** <br/> |
| Picas  <br/> | p  <br/> |**visPicas (51)** <br/> |
| Points  <br/> | pt  <br/> |**visPoints (50)** <br/> |
| Radians  <br/> | rad  <br/> |**visRadians (83)** <br/> |
| Seconds  <br/> | "  <br/> |**visSec (85)** <br/> |
| Yards  <br/> | yd  <br/> |**visYards (75)** <br/> |
   
## Compound units of measure

In formulas, you can express units of measure for compound numbers using the abbreviations in the following table. Visio simplifies the results and displays them in the compound units.
  
For example, if you enter 45.635°, Visio displays the equivalent value as 45° 38' 6".
  
|**To specify units**|**Use this abbreviation**|**Automation constant**|
|:-----|:-----|:-----|
| Ciceros and didots  <br/> | CICERO/DIDOT  <br/> |**visCicerosAndDidots (52)** <br/> |
| Degrees, minutes, and seconds  <br/> | °  <br/> |**visDegreeMinSec (82)** <br/> |
| Feet and inches  <br/> | FEET/INCH  <br/> |**visFeetAndInches (67)** <br/> |
| Picas and points  <br/> | PICAPOINTS  <br/> |**visPicasAndPoints (49)** <br/> |
   
## Fractional units of measure

You can specify fractional units of measure in the **DrawingScale** cell to affect the number of ruler subdivisions that Visio displays in the drawing window. By default, Visio divides distances into tenths when drawing its rulers. If you use fractional units of measure in the **DrawingScale** cell, Visio divides distance into the following: 
  
- Eighths for  *visInchFrac*  and  *visMileFrac* 
    
- Twelfths for  *visFeetAndInches* 
    
Fractional units of measure have no effect in cells other than in the DrawingScale cell.
  
|**To specify fractional units**|**Use this abbreviation**|**Automation constant**|
|:-----|:-----|:-----|
| Inches in fractions  <br/> | IN_F  <br/> |**visInchFrac (73)** <br/> |
| Miles in fractions  <br/> | MI_F  <br/> |**visMileFrac (74)** <br/> |
| Feet and inches  <br/> | FEET/INCH  <br/> |**visFeetAndInches (67)** <br/> |
   
## Multidimensional units of measure

In formulas, you can express units of measure for multidimensional numbers using the abbreviations in the following table. Visio simplifies the results and displays them in the multidimensional units.
  
|**To specify multidimensional units**|**Use this abbreviation**|**Automation constant**|
|:-----|:-----|:-----|
| Acre  <br/> | ACRES  <br/> |**visAcre (36)** <br/> |
| Centimeters  <br/> | SQ. CM., SQ CM, CM.^2, CM^2  <br/> |**visCentimeters (69)** <br/> |
| Feet  <br/> | SQ. FT., SQ FT, FT.^2, FT^2  <br/> |**visFeet (66)** <br/> |
| Hectare  <br/> | HECTARES, HECTARE, HA., HA  <br/> |**visHectare (37)** <br/> |
| Inches  <br/> | SQ. IN., SQ IN, IN.^2, IN^2  <br/> |**visInches (65)** <br/> |
| Kilometers  <br/> | SQ. KM., SQ KM, KM.^2, KM ^2  <br/> |**visKilometers (72)** <br/> |
| Meters  <br/> | SQ. M., SQ M, M.^2, M ^2  <br/> |**visMeters (71)** <br/> |
| Miles  <br/> | SQ. MI., SQ MI, MI.^2, MI ^2  <br/> |**visMiles (68)** <br/> |
| Millimeters  <br/> | SQ. MM., SQ MM, MM.^2, MM ^2  <br/> |**visMillimeters (70)** <br/> |
| Yards  <br/> | SQ. YD., SQ YD, YD.^2, YD^2  <br/> |**visYards (75)** <br/> |
   
## Universal strings

In localized versions of Visio, the set of recognized strings changes with the language. If you want your program to work with multiple languages, use the universal strings for units of measure.
  
|**For**|**Use**|
|:-----|:-----|
| Centimeters  <br/> | CM  <br/> |
| Ciceros  <br/> | C  <br/> |
| Ciceros and didots  <br/> | CICERO/DIDOT  <br/> |
| Date or time  <br/> | DATE  <br/> |
| Degrees  <br/> | DEG  <br/> |
| Degrees, minutes, seconds  <br/> | °  <br/> |
| Didots  <br/> | D  <br/> |
| Elapsed week  <br/> | EW  <br/> |
| Elapsed day  <br/> | ED  <br/> |
| Elapsed hour  <br/> | EH  <br/> |
| Elapsed minute  <br/> | EM  <br/> |
| Elapsed second  <br/> | ES  <br/> |
| Feet  <br/> | FT  <br/> |
| Feet and inches  <br/> | FEET/INCH  <br/> |
| Inches  <br/> | IN  <br/> |
| Inches in fractions  <br/> | IN_F  <br/> |
| Kilometers  <br/> | KM  <br/> |
| Meters  <br/> | M  <br/> |
| Miles  <br/> | MI  <br/> |
| Miles in fractions  <br/> | MI_F  <br/> |
| Millimeters  <br/> | MM  <br/> |
| Minutes  <br/> | '  <br/> |
| Nautical miles  <br/> | NM  <br/> |
| Percent  <br/> | %  <br/> |
| Picas  <br/> | P  <br/> |
| Picas and points  <br/> | PICAPOINTS  <br/> |
| Points  <br/> | PT  <br/> |
| Radians  <br/> | RAD  <br/> |
| Seconds  <br/> | "  <br/> |
| Yards  <br/> | YD  <br/> |
   
## Implicit units of measure

When Visio parses and stores a number-unit pair, it can use explicit units or implicit units. A number expressed in explicit units always is displayed in the units of measure that were originally entered. A number expressed in implicit units always converts to the equivalent value in the drawing, page, or angular units appropriate for the cell.
  
For example, suppose you enter the equivalent of 1 inch in cell A using explicit units and in cell B using implicit units, and that both cell A and cell B use drawing units. Next, you change the default units for the page to centimeters. Cell A still displays 1 in., because it uses explicit units that don't change with the defaults. Cell B now displays 2.54 cm, the equivalent value in the default units.
  
To enter units implicitly, use the following syntax.
  
```vb
number  [unit , flag ]
```

|||
|:-----|:-----|
| _number_ <br/> |The original value, such as 3.7, 1.7E-4, or 5 1/2.  <br/> |
| _unit_ <br/> |The units in which  _number_ originally is expressed.  <br/> |
| _flag_ <br/> |The measurement system to use when the implicit-value unit is displayed. See below for values.  <br/> |
   
The parameter  _flag_ is one of the following letters (either uppercase or lowercase) indicating the measurement system that should be used when the implicit-value unit is displayed. 
  
|**_Flag_**|**Measurement system**|**Example**|
|:-----|:-----|:-----|
| a, A  <br/> | Angular  <br/> | =5[deg,A]  <br/> |
| d, D  <br/> | Drawing  <br/> | =5[in,D]  <br/> |
| e, E  <br/> | Duration  <br/> | =5[eh,E]  <br/> |
| p, P  <br/> | Page  <br/> | =5[in,P]  <br/> |
| t, T  <br/> | Type  <br/> | =5[pt,T]  <br/> |
   
Additionally, you can use the implicit units DL, DP, DT, DA, DE for implicit drawing-, page-, text-, angular-, and time-units, respectively. These units assume the associated value is internal units. For example, if the current measurement system is centimeters,  *=2 DL*  would be interpreted as 2 internal units (inches) and displayed as 5.08 cm. 
  
Using the implicit syntax described above, this expression (=2 DL) is equivalent to 2[in,d]. The implicit syntax gives you the choice of how to interpret the value, so you could also specify 2[ft,d], which would be interpreted as 2 feet, and displayed as 60.96 cm. The implicit units DL, DP, DT, DA, and DE are universal, and do not have localized counterparts.
  
## Default units of measure

Following are the default units of measure along with their equivalent settings in the user interface.
  
|**Default unit of measure**|**User interface equivalent**|
|:-----|:-----|
|**visDrawingUnits** <br/> |The units in the DrawingScale cell of the page or master containing the cell.  <br/> |
|**visPageUnits** <br/> |The units selected in the **Measurement units** box on the **Page Properties** tab of the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow).  <br/> |
|**visTypeUnits** <br/> |The units selected in the **Text** box under **Display** on the **Advanced** tab of the **Visio Options** dialog box (click the **File** tab, and then click **Options**).  <br/> |
|**visAngleUnits** <br/> |The units selected in the **Angle** box under **Display** on the **Advanced** tab of the **Visio Options** dialog box.  <br/> |
|**visDurationUnits** <br/> |The units selected in the **Duration** box under **Display** on the **Advanced** tab of the **Visio Options** dialog box.  <br/> |
   

