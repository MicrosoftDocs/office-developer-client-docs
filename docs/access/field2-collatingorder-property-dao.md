---
title: "Field2.CollatingOrder Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: cb1d6fc9-a2a6-54c2-abf5-48b609e38738
description: "Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only Long ."
---

# Field2.CollatingOrder Property (DAO)

Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only **Long**. 
  
## Syntax

 *expression*  . **CollatingOrder**
  
 *expression*  A variable that represents a **Field2** object. 
  
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
   
The availability of the **CollatingOrder** property depends on the object that contains the **Fields** collection, as shown in the following table. 
  
|**If the Fields collection belongs to an**|**Then CollatingOrder is**|
|:-----|:-----|
|**Index** object  <br/> |Not supported  <br/> |
|**QueryDef** object  <br/> |Read-only  <br/> |
|**Recordset** object  <br/> |Read-only  <br/> |
|**Relation** object  <br/> |Not supported  <br/> |
|**TableDef** object  <br/> |Read-only  <br/> |
   
The **CollatingOrder** property setting corresponds to the  _locale_ argument of the **CreateDatabase** method when the database was created or the **CompactDatabase** method when the database was most recently compacted. 
  
The **CollatingOrder** and **Attributes** property settings of a **Field2** object in a **Fields** collection of an **Index** object together determine the sequence and direction of the sort order in an index. However, you can't set a collating order for an individual index— you can only set it for an entire table. 
  

