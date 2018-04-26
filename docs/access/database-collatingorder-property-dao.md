---
title: "Database.CollatingOrder Property (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 7f6c35bf-e5f9-8423-608e-bc072ca09141
description: "Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only Long ."
---

# Database.CollatingOrder Property (DAO)

Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only **Long**. 
  
## Syntax

 *expression*  . **CollatingOrder**
  
 *expression*  A variable that represents a **Database** object. 
  
## Remarks

The return value is a **Long** value or constant that can be one of the following values. 
  
|**Constant**|**Sort order**|
|:-----|:-----|
|**dbSortGeneral** <br/> |General (English, French, German, Portuguese, Italian, and Modern Spanish)  <br/> |
|**dbSortArabic** <br/> |Arabic  <br/> |
|**dbSortChineseSimplified** <br/> |Simplified Chinese  <br/> |
|**dbSortChineseTraditional** <br/> |Traditional Chinese  <br/> |
|**dbSortCyrillic** <br/> |Russian  <br/> |
|**dbSortCzech** <br/> |Czech  <br/> |
|**dbSortDutch** <br/> |Dutch  <br/> |
|**dbSortGreek** <br/> |Greek  <br/> |
|**dbSortHebrew** <br/> |Hebrew  <br/> |
|**dbSortHungarian** <br/> |Hungarian  <br/> |
|**dbSortIcelandic** <br/> |Icelandic  <br/> |
|**dbSortJapanese** <br/> |Japanese  <br/> |
|**dbSortKorean** <br/> |Korean  <br/> |
|**dbSortNeutral** <br/> |Neutral  <br/> |
|**dbSortNorwDan** <br/> |Norwegian or Danish  <br/> |
|**dbSortPDXIntl** <br/> |Paradox International  <br/> |
|**dbSortPDXNor** <br/> |Paradox Norwegian or Danish  <br/> |
|**dbSortPDXSwe** <br/> |Paradox Swedish or Finnish  <br/> |
|**dbSortPolish** <br/> |Polish  <br/> |
|**dbSortSlovenian** <br/> |Slovenian  <br/> |
|**dbSortSpanish** <br/> |Spanish  <br/> |
|**dbSortSwedFin** <br/> |Swedish or Finnish  <br/> |
|**dbSortThai** <br/> |Thai  <br/> |
|**dbSortTurkish** <br/> |Turkish  <br/> |
|**dbSortUndefined** <br/> |Undefined or unknown  <br/> |
   
The **CollatingOrder** property setting corresponds to the  _locale_ argument of the **CreateDatabase** method when the database was created or the **CompactDatabase** method when the database was most recently compacted. 
  
Check the **CollatingOrder** property setting of a **Database** or **Field** object to determine the string comparison method for the database or field. You can set the **CollatingOrder** property of a new, unappended **Field** object if you want the setting of the **Field** object to differ from that of the **Database** object that contains it. 
  

