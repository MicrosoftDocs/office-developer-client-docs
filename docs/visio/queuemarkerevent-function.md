---
title: "QUEUEMARKEREVENT Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60107
 
ms.localizationpriority: medium
ms.assetid: b4671715-4209-7774-c174-c19dc9721a02
description: "Causes the application to fire a marker event to your add-on, Microsoft Visual Basic for Applications (VBA) code, or COM add-in."
---

# QUEUEMARKEREVENT Function

Causes the application to fire a marker event to your add-on, Microsoft Visual Basic for Applications (VBA) code, or COM add-in.
  
## Syntax

QUEUEMARKEREVENT (***event_string*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *event_string* <br/> |Required  <br/> |**String** <br/> | The string to pass to your event handler. |

## Remarks

The QUEUEMARKEREVENT function provides developers with a way to notify their code from a ShapeSheet cell, and pass solution-specific information. When the cell containing the formula with the QUEUEMARKEREVENT function is evaluated, the application fires a marker event and passes *event_string* to all event handlers that are listening to the **MarkerEvent** event.
  
For more information about marker events, see the **QueueMarkerEvent** method and **MarkerEvent** event topics in the Microsoft Visio Automation Reference.
  
## Example

QUEUEMARKEREVENT ("MyCustomNotification")
  
Causes the application to fire a marker event, and passes the string "MyCustomNotification" to event handlers that are listening to the **MarkerEvent** event.
  