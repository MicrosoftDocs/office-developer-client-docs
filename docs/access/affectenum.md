---
title: "AffectEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 15393398-d7eb-a685-1bfa-d6712d8e5015
---

# AffectEnum

Specifies which records are affected by an operation.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adAffectAll** <br/> |3  <br/> |If there is not a [Filter](filter-property-ado.md) applied to the **Recordset**, affects all records. If the **Filter** property is set to a string criteria (such as "Author='Smith'"), then the operation affects visible records in the current chapter. If the **Filter** property is set to a member of the [FilterGroupEnum](filtergroupenum.md) or an array of Bookmarks, then the operation will affect all rows of the **Recordset**.  <br/> > [!NOTE]> adAffectAll is hidden in the Visual Basic Object Browser.           |
|**adAffectAllChapters** <br/> |4  <br/> |Affects all records in all sibling chapters of the **Recordset**, including those not visible via any **Filter** that is currently applied.  <br/> |
|**adAffectCurrent** <br/> |1  <br/> |Affects only the current record.  <br/> |
|**adAffectGroup** <br/> |2  <br/> |Affects only records that satisfy the current [Filter](filter-property-ado.md) property setting. You must set the **Filter** property to a **FilterGroupEnum** value or an array of **Bookmarks** to use this option.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.Affect.ALL  <br/> |
|AdoEnums.Affect.ALLCHAPTERS  <br/> |
|AdoEnums.Affect.CURRENT  <br/> |
|AdoEnums.Affect.GROUP  <br/> |
   

