---
title: "ComplexScriptFont Cell (Character Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60034
 
localization_priority: Normal
ms.assetid: e1cf9e97-101b-384f-65fe-0169c89dfccc

description: "Contains the number of the font used to format text composed of complex script characters. Font numbers vary according to the fonts installed on your system."
---

# ComplexScriptFont Cell (Character Section)

Contains the number of the font used to format text composed of complex script characters. Font numbers vary according to the fonts installed on your system. 
  
## Remarks

Complex script font sizes are listed on the **Font** tab in the **Text** dialog box (click the arrow in the **Font** group on the **Home** tab). This list appears only if you have added a language that contains Asian or complex script characters, in the **Microsoft Office Language Preferences** dialog box. (Click **Start**, click **All Programs**, click **Microsoft Office**, click **Microsoft Office Tools**, and then click **Microsoft Office Language Preferences**.
  
The number 0 (zero) means no font is specified. The Latin font or default fonts are used.
  
To get a reference to the ComplexScriptSize cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Char.ComplexScriptFont[ *i*  ]           where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the ComplexScriptFont cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionCharacter** <br/> |
|Row index:  <br/> |**visRowCharacter** +  *i*           where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visCharacterComplexScriptFont** <br/> |
   

