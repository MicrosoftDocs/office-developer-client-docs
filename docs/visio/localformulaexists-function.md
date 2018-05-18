---
title: "LOCALFORMULAEXISTS Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60105
 
localization_priority: Normal
ms.assetid: 2b757c8d-7732-0f9b-c836-ef755dd1c673
description: "Indicates whether the referenced cell contains a local formula."
---

# LOCALFORMULAEXISTS Function

Indicates whether the referenced cell contains a local formula. 
  
## Syntax

LOCALFORMULAEXISTS ( ** *cellref* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellref_ <br/> |Required  <br/> |**String** <br/> | The cell that you want to check for the presence of a formula.  <br/> |
   
### Return value

Boolean
  
## Remarks

The LOCALFORMULAEXISTS function returns 1 if the cell contains a local formula; if there is no formula, or if the formula is inherited, it returns 0 (zero). 
  

