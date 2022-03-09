---
title: "AsianFont Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033764
 
ms.localizationpriority: medium
ms.assetid: 45bfaaaa-52cc-f8b4-68e7-8b99e5788ce1

description: "Contains the number of the font used to format the text containing Asian characters. Font numbers vary according to the fonts installed on your system."
---

# AsianFont Cell (Character Section)

Contains the number of the font used to format the text containing Asian characters. Font numbers vary according to the fonts installed on your system. 
  
## Remarks

Asian fonts are listed on the **Font** tab in the **Text** dialog box (click the arrow in the **Font** group on the **Home** tab). This list appears only if you have added a language that contains Asian or complex script characters, in the **Microsoft Office Language Preferences** dialog box. (Click **Start**, click **All Programs**, click **Microsoft Office**, click **Microsoft Office Tools**, and then click **Microsoft Office Language Preferences**.
  
The number 0 means no font is specified. The Latin font or default fonts are used if they contain the necessary characters.
  
To get a reference to the AsianFont cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Char.AsianFont[ *i*  ]           where  *i*  = <1>, 2, 3... |
   
To get a reference to the AsianFont cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionCharacter** <br/> |
|**Row index:**  <br/> |**visRowCharacter** +  *i*           where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visCharacterAsianFont** <br/> |
   

