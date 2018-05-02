---
title: "ConFixedCode Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm175
 
localization_priority: Normal
ms.assetid: 8e7c9080-7ef1-0696-a3d2-d8f57ea5ab9b
description: "Determines when a connector reroutes."
---

# ConFixedCode Cell (Shape Layout Section)

Determines when a connector reroutes.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Reroute freely  <br/> |**visSLOConFixedRerouteFreely** <br/> |
|1  <br/> |Reroute as needed (manual reroute)  <br/> |**visSLOConFixedRerouteAsNeeded** <br/> |
|2  <br/> |Never reroute  <br/> |**visSLOConFixedRerouteNever** <br/> |
|3  <br/> |Reroute on crossover  <br/> |**visSLOConFixedRerouteOnCrossover** <br/> |
|4  <br/> |For internal use only  <br/> |**visSLOConFixedByAlgFrom** <br/> |
|5  <br/> |For internal use only  <br/> |**visSLOConFixedByAlgTo** <br/> |
|6  <br/> |For internal use only  <br/> |**visSLOConFixedByAlgFromTo** <br/> |
   
## Remarks

You can also set the value of this cell by selecting a dynamic connector, clicking **Behavior** in the **Shape Design** group on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then clicking the **Connector** tab. 
  
To get a reference to the ConFixedCode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ConFixedCode  <br/> |
   
To get a reference to the ConFixedCode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLOConFixedCode** <br/> |
   

