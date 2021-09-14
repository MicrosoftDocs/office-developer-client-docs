---
title: "ISERR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251448
 
ms.localizationpriority: medium
ms.assetid: 87508007-8ad2-3bcf-55dc-f0207c7c6fe3
description: "Returns TRUE if the value of cellreference is any error type except #N/A; otherwise, it returns FALSE. The ISERR function is used in formulas that refer to another cell."
---

# ISERR Function

Returns TRUE if the value of  _cellreference_ is any error type except #N/A; otherwise, it returns FALSE. The ISERR function is used in formulas that refer to another cell. 
  
## Syntax

ISERR(** *cellreference* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellreference_ <br/> |Required  <br/> |**String** <br/> |Reference to a cell.  <br/> |
   
## Example 1

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.A1  <br/> |=NA( )  <br/> |#N/A!  <br/> |
|Scratch.B1  <br/> |=ISERR(Scratch.A1)  <br/> |FALSE  <br/> |
   
Returns FALSE because the #N/A! error is not recognized by the ISERR function. Use ISERROR to find all error types.
  
## Example 2

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.X1  <br/> |="House"  <br/> |#VALUE!  <br/> |
|Scratch.A1  <br/> |=ISERR(Scratch.X1)  <br/> |TRUE  <br/> |
   
Returns TRUE because the #VALUE! error is recognized by the ISERR function.
  

