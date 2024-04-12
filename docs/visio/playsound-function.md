---
title: "PLAYSOUND Function"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251479
 
ms.localizationpriority: medium
ms.assetid: 098d216f-e699-0e74-f702-ccfa7809c19b
description: "Plays a sound file or system sound."
---

# PLAYSOUND Function

Plays a sound file or system sound.
  
## Syntax

PLAYSOUND(" ***filename*** "|" ***alias*** ", ***isAlias***, ***beep***, ***synch*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *filename* <br/> |Required  <br/> |**String** <br/> |The name of the sound file you want to play. |
| *alias* <br/> |Required  <br/> |**String** <br/> | A system sound represented by an alias. |
| *isAlias* <br/> |Required  <br/> |**Boolean** <br/> | Specifies whether the preceding expression is an alias or file name; use a non-zero value to specify an alias. |
| *beep* <br/> |Required  <br/> |**Boolean** <br/> |Specifies whether Microsoft Visio beeps when sound can't be played; use a non-zero number to beep. |
| *synch* <br/> |Required  <br/> |**Boolean** <br/> |Determines whether sounds are played asynchronously (0) or synchronously (1). |

## Remarks

You should usually play sounds asynchronously so that Visio can continue processing while it plays the sound. To string several sounds together, play them synchronously, or some might fail to play.
  
## Example 1

PLAYSOUND("chord.wav", 0, 0, 0)
  
Plays the wave audio file chord.wav asynchronously with no warning beep.
  
## Example 2

PLAYSOUND("SystemExclamation", 1, 0, 0)
  
Plays the system exclamation sound asynchronously with no warning beep.
  