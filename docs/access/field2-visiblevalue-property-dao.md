---
title: "Field2.VisibleValue Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1101184
  
localization_priority: Normal
ms.assetid: 1e023a1a-fd49-7570-42bd-2f4c06ac5e5e

---

# Field2.VisibleValue Property (DAO)

## Syntax

 *expression*  . **VisibleValue**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

This property contains the value of the field that is currently in the database on the server. During an optimistic batch update, a collision may occur where a second client modified the same field and record in between the time the first client retrieved the data and the first client's update attempt. When this happens, the value that the second client set will be accessible through this property.
  

