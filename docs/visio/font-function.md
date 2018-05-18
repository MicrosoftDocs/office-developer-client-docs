---
title: "FONT Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 20b587ee-87bf-4648-99ec-ddedd703d9fd
description: "Returns the integer value of the unique identifier for a font, specified by name."
---

# FONT Function

Returns the integer value of the unique identifier for a font, specified by name.
  
> [!NOTE]
> In most cases, the font identifier is system-specific. Although the font remains established once used in a file, the **FONT** function provides consistent access to a particular font across systems and versions of Visio. It is recommended that you use the **FONT** function to assign fonts instead of referring to font identifiers directly. 
  
## Version Information

Version Added: Visio 2013 
  
## Syntax

 **FONT**( _"font_name_string"_)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _font_name_string_ <br/> |Required  <br/> |**string** <br/> |The name of the font.  <br/> |
   
## Return value

Integer
  
## Remarks

If the string provided for  *font_name_string*  does not match a known font, this function returns a #VALUE! error. 
  
## Example

 `FONT("Calibri")`
  
Returns the integer value (4) representing the unique ID for the "Calibri" font.
  

