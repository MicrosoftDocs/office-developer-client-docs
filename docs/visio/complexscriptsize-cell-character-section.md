---
title: "ComplexScriptSize Cell (Character Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033768
 
localization_priority: Normal
ms.assetid: f58687d7-2ba4-ff77-0bcc-3106867d89de

description: "The size of the font used to format text composed of complex script characters."
---

# ComplexScriptSize Cell (Character Section)

The size of the font used to format text composed of complex script characters. 
  
## Remarks

Complex script font sizes are listed on the **Font** tab in the **Text** dialog box (click the arrow in the **Font** group on the **Home** tab). This list appears only if you have added a language that contains Asian or complex script characters, in the **Microsoft Office Language Preferences** dialog box. (Click **Start**, click **All Programs**, click **Microsoft Office**, click **Microsoft Office Tools**, and then click **Microsoft Office Language Preferences**.
  
You can enter this value as an explicit point size or as a percentage. If you specify a percentage, the value is based on the value in the Size cell. A default value of 0 (zero) means 100%. 
  
To get a reference to the ComplexScriptSize cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Char.ComplexScriptSize[ *i*  ]           where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the ComplexScriptSize cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionCharacter** <br/> |
|Row index:  <br/> |**visRowCharacter** +  *i*           where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visCharacterComplexScriptSize** <br/> |
   

