---
title: "Field.VisibleValue Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e40fcb43-9a1d-69e7-1544-8f15ef21daf4

---

# Field.VisibleValue Property (DAO)

## Syntax

 *expression*  . **VisibleValue**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

This property contains the value of the field that is currently in the database on the server. During an optimistic batch update, a collision may occur where a second client modified the same field and record in between the time the first client retrieved the data and the first client's update attempt. When this happens, the value that the second client set will be accessible through this property.
  

