---
title: "OPENFILE Function"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251471
 
ms.localizationpriority: medium
ms.assetid: ff59ab04-a589-cf9e-db3b-20658a7dffdc
description: "Opens a Microsoft Visio document, if it's not already open, and activates the document window."
---

# OPENFILE Function

Opens a Microsoft Visio document, if it's not already open, and activates the document window.
  
## Syntax

 **OPENFILE**( _"filename"_)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _filename_ <br/> |Required  <br/> |**String** <br/> |The name of the file, including file path, you want to open. |
   
## Remarks

Multiple OPENFILE function calls are queued and executed in order of evaluation. If the current Visio document is activated for visual (in-place) editing, a new Visio instance is launched with the requested file name. 
  
This function always returns FALSE. 
  
In earlier versions of the Visio application, this function appears as _OPENFILE. Visio versions 4.0 and later accept either style. 
  
## Example

 `OPENFILE("C:/MyFile.vsdx")`
  
Opens the specified file "MyFile.vsdx" in a new window, or activates the window if the file is already open. 
  

