---
title: "THEMEVAL Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 9eac3b8c-532c-4312-935d-fe8b63bcaf75
description: "Retrieves values from the active theme."
---

# THEMEVAL Function

Retrieves values from the active theme. 
  
## Version Information

Version Added: Visio 2013 
  
## Syntax

 **THEMEVAL**([ _"theme_value"_][, _default_]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _"theme_value"_ <br/> |Optional  <br/> |**String** <br/> |The name of a cell in the theme definition to get a value from.  <br/> |
| _default_ <br/> |Optional  <br/> |Various  <br/> |A default value if the document is not themed (there is no theme definition).  <br/> |
   
## Remarks

If the **THEMEVAL** function does not receive any arguments, it returns the themed value of the host cell. This is the value stored in the definition of the current theme. The host cell must be capable of being themed to return a value; if the cell is not capable of being themed, **THEMEVAL** returns an error. 
  
If the **THEMEVAL** function receives a single argument, it retrieves the value from the theme definition passed in as the argument. The argument passed in for the first parameter must be an integer or one of the exact strings listed in the table below. 
  
The **THEMEVAL** function can also accept an integer for the first parameter, as a value between 1 and 8. Using integer values retrieves a color by index from the color scheme of the theme. Thus, a value of '1' will return the "Dark" color from the theme, '2' returns the "Light" color, '3' returns the "Accent 1" color, etc. 
  
If the **THEMEVAL** function receives two arguments, it retrieves the value from the theme definition passed in as the first argument. However, if the document has No Theme applied to it, then the **THEMEVAL** function uses the value specified as the second argument. 
  
**Possible arguments for the "theme_value" parameter**

|**Value**|**Description**|
|:-----|:-----|
|"Dark"  <br/> |Retrieves Dark RGB color from the theme definition.  <br/> |
|"Light"  <br/> |Retrieves Light RGB color from the theme definition.  <br/> |
|"BackgroundColor"  <br/> |Retrieves Background RGB color from the theme definition.  <br/> |
|"AccentColor"  <br/> |Retrieves Accent1 RGB color from the theme definition.  <br/> |
|"AccentColor2"  <br/> |Retrieves Accent2 RGB color from the theme definition.  <br/> |
|"AccentColor3"  <br/> |Retrieves Accent3 RGB color from the theme definition.  <br/> |
|"AccentColor4"  <br/> |Retrieves Accent4 RGB color from the theme definition.  <br/> |
|"AccentColor5"  <br/> |Retrieves Accent5 RGB color from the theme definition.  <br/> |
|"AccentColor6"  <br/> |Retrieves Accent6 RGB color from the theme definition.  <br/> |
|"LinePattern"  <br/> |Retrieves LinePattern cell value from the theme definition.  <br/> |
|"LineWeight"  <br/> |Retrieves LineWeight cell value from the theme definition.  <br/> |
|"LineColor"  <br/> |Retrieves LineColor cell value from the theme definition.  <br/> |
|"LineCap"  <br/> |Retrieves LineCap cell value from the theme definition.  <br/> |
|"LineBegin"  <br/> |Retrieves BeginArrow cell value from the theme definition.  <br/> |
|"LineEnd"  <br/> |Retrieves EndArrow cell value from the theme definition.  <br/> |
|"LineColorTrans"  <br/> |Retrieves LineColorTrans cell value from the theme definition.  <br/> |
|"LineCompoundtype"  <br/> |Retrieves CompoundType cell value from the theme definition.  <br/> |
|"LineBegin"  <br/> |Retrieves BeginArrow cell value from the theme definition.  <br/> |
|"LineEnd"  <br/> |Retrieves EndArrow cell value from the theme definition.  <br/> |
|"LineBeginSize"  <br/> |Retrieves BeginArrowSize cell value from the theme definition.  <br/> |
|"LineEndSize"  <br/> |Retrieves EndArrowSize cell value from the theme definition.  <br/> |
|"LineRounding"  <br/> |Retrieves Rounding cell value from the theme definition.  <br/> |
|"ConnectorColor"  <br/> |Retrieves LineColor cell value from the theme definition.  <br/> |
|"ConnectorPattern"  <br/> |Retrieves LinePattern cell value from the theme definition.  <br/> |
|"ConnectorWeight"  <br/> |Retrieves LineWeight cell value from the theme definition.  <br/> |
|"ConnectorTransparency"  <br/> |Retrieves LineColorTrans cell value from the theme definition.  <br/> |
|"ConnectorRounding"  <br/> |Retrieves Rounding cell value from the theme definition.  <br/> |
|"ConnectorBegin"  <br/> |Retrieves BeginArrow cell value from the theme definition.  <br/> |
|"ConnectorEnd"  <br/> |Retrieves EndArrow cell value from the theme definition.  <br/> |
|"ConnectorBeginSize"  <br/> |Retrieves BeginArrowSize cell value from the theme definition.  <br/> |
|"ConnectorEndSize"  <br/> |Retrieves EndArrowSize cell value from the theme definition.  <br/> |
|"FillColor"  <br/> |Retrieves FillForegnd cell value from the theme definition.  <br/> |
|"FillColor2"  <br/> |Retrieves FillBkgnd cell value from the theme definition.  <br/> |
|"FillTransparency"  <br/> |Retrieves FillForegndTrans cell value from the theme definition.  <br/> |
|"FillPattern"  <br/> |Retrieves FillPattern cell value from the theme definition.  <br/> |
|"LineGradientEnabled"  <br/> |Retrieves LineGradientEnabled cell value from the theme definition.  <br/> |
|"LineGradientDir"  <br/> |Retrieves LineGradientDir cell value from the theme definition.  <br/> |
|"LineGradientAngle"  <br/> |Retrieves LineGradientAngle cell value from the theme definition.  <br/> |
|"FillGradientEnabled"  <br/> |Retrieves FillGradientEnabled cell value from the theme definition.  <br/> |
|"FillGradientDir"  <br/> |Retrieves FillGradientDir cell value from the theme definition.  <br/> |
|"FillGradientAngle"  <br/> |Retrieves FillGradientAngle cell value from the theme definition.  <br/> |
|"RotateGradientWithShape"  <br/> |Retrieves RotateGradientWithShape cell value from the theme definition.  <br/> |
|"UseGroupGradient"  <br/> |Retrieves UseGroupGradient cell value from the theme definition.  <br/> |
|"ShadowType"  <br/> |Retrieves ShapeShdwType cell value from the theme definition.  <br/> |
|"ShadowColor"  <br/> |Retrieves ShdwColor cell value from the theme definition.  <br/> |
|"ShadowTransparency"  <br/> |Retrieves ShdwColorTrans cell value from the theme definition.  <br/> |
|"ShadowMagnification"  <br/> |Retrieves ShapeShdwScaleFactor cell value from the theme definition.  <br/> |
|"ShadowBlur"  <br/> |Retrieves ShapeShdwBlur cell value from the theme definition.  <br/> |
|"ShadowXOffset"  <br/> |Retrieves ShapeShdwOffsetX cell value from the theme definition.  <br/> |
|"ShadowYOffset"  <br/> |Retrieves ShapeShdwOffsetY cell value from the theme definition.  <br/> |
|"ShadowDirection"  <br/> |Retrieves ShapeShdwObliqueAngle cell value from the theme definition.  <br/> |
|"ShadowPattern"  <br/> |Retrieves ShdwPattern cell value from the theme definition.  <br/> |
|"BevelTopType"  <br/> |Retrieves BevelTopType cell value from the theme definition.  <br/> |
|"BevelTopWidth"  <br/> |Retrieves BevelTopWidth cell value from the theme definition.  <br/> |
|"BevelTopHeight"  <br/> |Retrieves BevelTopHeight cell value from the theme definition.  <br/> |
|"BevelMaterial"  <br/> |Retrieves BevelMaterialType cell value from the theme definition.  <br/> |
|"BevelLighting"  <br/> |Retrieves BevelLightingType cell value from the theme definition.  <br/> |
|"BevelLightingAngle"  <br/> |Retrieves BevelLightingAngle cell value from the theme definition.  <br/> |
|"BevelContourColor"  <br/> |Retrieves BevelContourColor cell value from the theme definition.  <br/> |
|"BevelContourSize"  <br/> |Retrieves BevelContourSize cell value from the theme definition.  <br/> |
|"ReflectionBlur"  <br/> |Retrieves ReflectionBlur cell value from the theme definition.  <br/> |
|"ReflectionDist"  <br/> |Retrieves ReflectionDist cell value from the theme definition.  <br/> |
|"ReflectionSize"  <br/> |Retrieves ReflectionSize cell value from the theme definition.  <br/> |
|"ReflectionTrans"  <br/> |Retrieves ReflectionTrans cell value from the theme definition.  <br/> |
|"SoftEdgesSize"  <br/> |Retrieves SoftEdgesSize cell value from the theme definition.  <br/> |
|"GlowSize"  <br/> |Retrieves GlowSize cell value from the theme definition.  <br/> |
|"GlowColor"  <br/> |Retrieves GlowColor cell value from the theme definition.  <br/> |
|"GlowTransparency"  <br/> |Retrieves GlowColorTrans cell value from the theme definition.  <br/> |
|"SketchAmount"  <br/> |Retrieves SketchAmount cell value from the theme definition.  <br/> |
|"SketchEnabled"  <br/> |Retrieves SketchEnabled cell value from the theme definition.  <br/> |
|"SketchFillChange"  <br/> |Retrieves SketchFillChange cell value from the theme definition.  <br/> |
|"SketchLineChange"  <br/> |Retrieves SketchLineChange cell value from the theme definition.  <br/> |
|"SketchLineWeight"  <br/> |Retrieves SketchLineWeight cell value from the theme definition.  <br/> |
|"LatinFont"  <br/> |Retrieves Font cell value from the theme definition.  <br/> |
|"TextColor"  <br/> |Retrieves Color cell value from the theme definition.  <br/> |
|"TextStyle"  <br/> |Retrieves the Character.Style cell value from the theme definition.  <br/> |
|"ComplexFont"  <br/> |Retrieves ComplexScriptFont cell value from the theme definition.  <br/> |
|"AsianFont"  <br/> |Retrieves AsianFont cell value from the theme definition.  <br/> |
|"FillStop[x]Color"  <br/> |Retrieves Color cell value in row  *x*  from the theme definition.  <br/> |
|"FillStop[x]Transparency"  <br/> |Retrieves ColorTrans cell value in row  *x*  from the theme definition.  <br/> |
|"FillStop[x]Position"  <br/> |Retrieves Position cell value in row  *x*  from the theme definition.  <br/> |
|"LineStop[x]Color"  <br/> |Retrieves Color cell value in row  *x*  from the theme definition.  <br/> |
|"LineStop[x]Transparency"  <br/> |Retrieves ColorTrans cell value in row  *x*  from the theme definition.  <br/> |
|"LineStop[x]Position"  <br/> |Retrieves Position cell value in row  *x*  from the theme definition.  <br/> |
   
## Example

 `THEMEVAL("5")`
  
Returns the "Accent 3" color from the theme definition.
  
 `THEMEVAL("LineWeight", "0.7 pt.")`
  
Returns the value of the "LineWeight" cell from the theme definition. If the shape containing this function has No Theme applied to it, the function returns '0.7 pt.'.
  

