---
title: "ISERRNA Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251451
 
ms.localizationpriority: medium
ms.assetid: 6ee7dc3d-efe9-c862-f71d-034b3d9c3ec6
description: "Returns TRUE if the value of cellreference is error type #N/A! (not available); otherwise, it returns FALSE. The ISERRNA function is used in formulas that refer to another cell."
---

# ISERRNA Function

Returns TRUE if the value of  _cellreference_ is error type #N/A! (not available); otherwise, it returns FALSE. The ISERRNA function is used in formulas that refer to another cell. 
  
## Syntax

ISERRNA(** *cellreference* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellreference_ <br/> |Required  <br/> |**String** <br/> |Reference to a cell. |
   
## Example 1

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.A1  <br/> |="5 + 3"  <br/> |"8"  <br/> |
|Scratch.B1  <br/> |=ISERRNA(Scratch.A1)  <br/> |FALSE  <br/> |
   
Returns FALSE because the value returned is available.
  
## Example 2

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.A1  <br/> |=NA( )  <br/> |#N/A!  <br/> |
|Scratch.B1  <br/> |=ISERRNA(Scratch.A1)  <br/> |TRUE  <br/> |
   
Returns TRUE because the value returned is error type #N/A!
  

