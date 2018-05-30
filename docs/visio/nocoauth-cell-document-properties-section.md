---
title: "NoCoauth Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 6f2095c9-ce09-48f7-b160-c9822d96a96c
description: "Sets whether a document stored on a Microsoft SharePoint 2013 server or Microsoft OneDrive can be edited by multiple authors simultaneously in a coauthoring session."
---

# NoCoauth Cell (Document Properties Section)

Sets whether a document stored on a Microsoft SharePoint 2013 server or Microsoft OneDrive can be edited by multiple authors simultaneously in a coauthoring session.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The document cannot be coauthored and is locked for editing when open.  <br/> |
|FALSE  <br/> |The document can be coauthored.  <br/> |
   
## Remarks

To get a reference to the **NoCoauth** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | NoCoauth  <br/> |
   
To get a reference to the **NoCoauth** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowDoc** <br/> |
| Cell index:  <br/> |**visDocNoCoauth** <br/> |
   

