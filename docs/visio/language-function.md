---
title: "LANGUAGE Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: e372c670-e9a0-4352-b70a-3a054b036124
description: "Allows comparison operations between different language representations. It is best used for converting Internet Engineering Task Force language tags (BCP 47) values to locale id (LCID) values."
---

# LANGUAGE Function

Allows comparison operations between different language representations. It is best used for converting Internet Engineering Task Force language tags (BCP 47) values to locale id (LCID) values.
  
## Version Information

Version Added: Visio 2013 
  
## Syntax

 **LANGUAGE**( _lcid_or_bcp47_)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _lcid_or_bcp47_ <br/> |Required  <br/> |**String** <br/> |The LCID or BCP 47 value for the language.  <br/> |
   
## Return value

Integer
  
## Example

 `LANGUAGE("en-us")`
  
Returns a value of '1033'.
  
 `LANGUAGE("es-es")`
  
Returns a value of '3082'.
  

