---
title: "HELP Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251436
 
ms.localizationpriority: medium
ms.assetid: 5b358c38-6ed1-3fbe-c1d1-1a56ebbaa870
description: "Opens an HTML Help file with the specifed keyword in the Search box."
---

# HELP Function

Opens an HTML Help file with the specifed  *keyword*  in the **Search** box.
  
## Syntax

HELP(" ***filename.chm!keyword*** ")
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *filename.chm!keyword* <br/> |Required  <br/> |**String** <br/> | The filename of the Help file and the keyword to search for. |

## Remarks

If no  *keyword*  is specified, the HELP function opens the contents page of the Help file.
  
## Example

HELP("visio.chm!shapesheet")
  
Opens the Visio Help file and displays a list of the topic(s) whose keyword is "shapesheet."
  