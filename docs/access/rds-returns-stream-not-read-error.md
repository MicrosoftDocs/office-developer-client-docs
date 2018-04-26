---
title: "RDS Returns 'Stream Not Read' Error"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 325f7b9d-8e71-bc2c-94e3-b4b4a1a2dc58
description: "The Stream object could not be read because it is empty, or the current position is at the end of the Stream. For non-empty Streams, set the current position with the Position property. To determine if a Stream is empty, check the Size property."
---

# RDS Returns "Stream Not Read" Error

"The Stream object could not be read because it is empty, or the current position is at the end of the Stream. For non-empty Streams, set the current position with the Position property. To determine if a Stream is empty, check the Size property."
  
If you get the error above, it may be a result of trying to use a parameterized hierarchical query over http. RDS does not permit you to remote parameterized hierarchies.
  

