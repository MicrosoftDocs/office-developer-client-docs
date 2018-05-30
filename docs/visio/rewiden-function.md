---
title: "REWIDEN Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033808
 
localization_priority: Normal
ms.assetid: c20842cd-86b1-83fa-49ba-118936013b6f
description: "Converts a formula that produces 16-bit character codes that are widened single-byte or multibyte character-set codes into a string of 16-bit Unicode character codes, using the specified character sets."
---

# REWIDEN Function

Converts a formula that produces 16-bit character codes that are widened single-byte or multibyte character-set codes into a string of 16-bit Unicode character codes, using the specified character sets. 
  
## Syntax

REWIDEN(** *srcCharSet* **, ** *dstCharSet* **, ** *text* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _srcCharSet_ <br/> |Required  <br/> |**String** <br/> |The character set in the source document.  <br/> |
| _dstCharSet_ <br/> |Required  <br/> |**String** <br/> | The character set in the destination document.  <br/> |
| _text_ <br/> |Required  <br/> |**String** <br/> |The text to convert.  <br/> |
   
## Remarks

The REWIDEN function is used in automatic conversion of Visio 2002 documents to Visio 2003 documents. Other use is not recommended.
  

