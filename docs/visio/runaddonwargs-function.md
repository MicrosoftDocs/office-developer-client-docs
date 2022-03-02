---
title: "RUNADDONWARGS Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251493
 
ms.localizationpriority: medium
ms.assetid: c154413f-c366-a66b-94e3-ed71ad23f325
description: "Runs string and passes the command line arguments to the program as a string."
---

# RUNADDONWARGS Function

Runs _string_ and passes the command line _arguments_ to the program as a string.
  
## Syntax

RUNADDONWARGS(" ** _string_ ** "," ** _arguments_ ** ")
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _string_ <br/> |Required  <br/> |**String** <br/> | The name of an add-on. |
| _arguments_ <br/> |Required  <br/> |**String** <br/> |Arguments to pass to your program. |

## Remarks

In practice, _arguments_ should be 50 or fewer characters. Use the RUNADDONWARGS function to bind a program, such as an add-on, to a cell, for example, to an Action or Events cell.
  
The RUNADDONWARGS function can only run add-ons that are members of the application's **Addons** collection. To be present in that collection, an add-on must be an EXE file or VSL file that is:
  
- Installed in the application's **Startup** or **Addons** path.

- Added programmatically by using the **Add** method of the **Addons** collection.

For more information about running code in Visio, see [About Security Settings and Running Code in Visio](about-security-settings-and-running-code-in-visio-shapesheet.md) in this ShapeSheet Reference.
  
In earlier versions of Visio, this function appears as _RUNADDONWARGS. Visio application versions 4.0 and later accept either style.
  
## Example

RUNADDONWARGS("GRAPHMKR.EXE","/GraphMaker=Stack")
  
Launches the add-on Graphmkr.exe and passes it the argument /GraphMaker=Stack.
  